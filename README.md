# ycyx-skills

> 多 Skill 容器仓库。每个 Skill 放在 `skills/<skill-name>/` 子目录下，独立维护、互不耦合。

[![Skills](https://img.shields.io/badge/skills-1-blue)](#skill-列表)
[![协议](https://img.shields.io/badge/license-MIT-lightgrey)](LICENSE)
[![文档规范](https://img.shields.io/badge/docs-Markdown%20only-green)](#文档规范)

---

## 一、这是什么

本仓库是 **Claude Code / Claude API Skill 的集中托管地**，按 Skill 拆分到独立子目录：

```
ycyx-skills/
├── README.md                          ← 本文件（仓库说明）
├── LICENSE                            ← MIT 协议
├── .gitignore
└── skills/
    ├── ycyx-artical/                  ← Skill: 玉柴研学文旅新媒体文案
    │   ├── SKILL.md                   ← Skill 主入口（YAML 元数据 + 工作流）
    │   ├── examples/                  ← 精选范例
    │   └── references/                ← 按需加载的参考资料
    ├── ycyx-foo/                      ← 未来的 Skill
    └── ycyx-bar/                      ← 未来的 Skill
```

每个 Skill 是一个**自包含单元**：

- `SKILL.md`：含 YAML frontmatter，Claude Code 自动识别并加载
- `references/`：按需加载的详细文档（业务底稿、规则、风格库等）
- `examples/`：精选范例与结构拆解

## 二、Skill 列表

| Skill | 路径 | 用途 | 文档 |
|---|---|---|---|
| **ycyx-artical** | `skills/ycyx-artical/` | 玉柴研学文旅公众号 + 视频号新媒体文案 AI 写作 | [SKILL.md](skills/ycyx-artical/SKILL.md) |

## 三、如何使用

### 在 Claude Code 中加载整个仓库

```bash
# 把整个仓库克隆到 Claude Code skills 目录
git clone https://github.com/KawasakiTakayuki/ycyx-skills.git ~/.claude/skills/ycyx-skills

# Claude Code 会自动扫描 SKILL.md 并启用所有 skill
# 或只把某个 skill 软链过去
ln -s ~/.claude/skills/ycyx-skills/skills/ycyx-artical ~/.claude/skills/ycyx-artical
```

### 在自定义智能体中使用

每个 Skill 的 `SKILL.md` 是入口；详细规则在 `references/`。参见各 Skill 自身的 README 与文档。

## 四、添加新 Skill

```bash
# 1. 在 skills/ 下创建子目录
mkdir -p skills/ycyx-foo/{examples,references}

# 2. 创建 SKILL.md（含 YAML frontmatter）
cat > skills/ycyx-foo/SKILL.md <<'EOF'
---
name: ycyx-foo
description: 一句话描述何时使用本 skill
---

# ycyx-foo · Skill 标题

正文内容...
EOF

# 3. 提交并推送
git add skills/ycyx-foo/
git commit -m "feat: 新增 ycyx-foo skill"
git push
```

详见 [skills/ycyx-artical/PUSH.md](skills/ycyx-artical/PUSH.md) 了解完整推送流程。

## 五、Skill 设计规范

每个 Skill 内部建议遵循以下约定（与 ycyx-artical 保持一致）：

| 文件/目录 | 用途 |
|---|---|
| `SKILL.md` | 主入口；含 YAML frontmatter（name + description）；总长建议 ≤ 5000 字 |
| `references/` | 按需加载的详细文档（业务、规则、风格、素材库等） |
| `examples/` | 精选范例 + 结构拆解 + 适用场景 |
| `README.md`（可选） | Skill 自身使用说明 |

**文档规范**：所有文档使用 Markdown 编写，无 .docx / .txt / .py 等其他格式。
- 文本可读、AI 可直接读写
- 版本控制友好（diff 清晰）
- 风格参考库、规则手册、素材库三类内容结构化组织

## 六、协议

[MIT](LICENSE) — 仓库结构部分；各 Skill 引用的业务内容版权归原公司所有。
