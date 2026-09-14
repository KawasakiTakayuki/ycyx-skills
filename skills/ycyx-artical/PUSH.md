# ycyx-skills 仓库协作指南

> 本文件介绍如何在 `ycyx-skills` 仓库中**新增 / 修改 / 推送 Skill**。

## 日常推送流程

```bash
cd /Volumes/Samsung980pro/AI/ycyx-artical     # 仓库根

# 编辑 / 创建文件后
git add skills/ycyx-artical/<改动文件>
git commit -m "feat(ycyx-artical): <简述改动>"
git push origin main
```

> 仓库使用 HTTPS，需 GitHub 用户名 + Personal Access Token（PAT）。
> 旧版密码已停用，到 https://github.com/settings/tokens 生成。

## 添加新 Skill（标准流程）

```bash
# 1. 创建 Skill 子目录结构
mkdir -p skills/ycyx-foo/{examples,references}

# 2. 创建 SKILL.md（含 YAML frontmatter）
cat > skills/ycyx-foo/SKILL.md <<'EOF'
---
name: ycyx-foo
description: 一句话描述何时使用本 skill（Claude 据此判断是否自动激活）
---

# ycyx-foo · Skill 标题

正文内容...
EOF

# 3. 添加 references 与 examples
cp <源文件> skills/ycyx-foo/references/业务简介.md
# ...

# 4. 更新仓库根 README.md（添加新 Skill 到列表）

# 5. 提交推送
git add skills/ycyx-foo/ README.md
git commit -m "feat: 新增 ycyx-foo skill"
git push
```

## 修改现有 Skill

```bash
# 直接编辑 skills/<skill-name>/ 下文件 → 提交推送
git add skills/ycyx-artical/<文件>
git commit -m "fix(ycyx-artical): <简述改动>"
git push
```

## 删除 Skill

```bash
git rm -r skills/ycyx-foo/
# 同步从仓库根 README.md 的 Skill 列表中移除
git commit -m "chore: 移除 ycyx-foo skill"
git push
```

## 切换 SSH（如已配 SSH key）

```bash
git remote set-url origin git@github.com:KawasakiTakayuki/ycyx-skills.git
```

## 注意事项

- 每个 Skill 必须有 `SKILL.md`（含 YAML frontmatter），否则 Claude 不会自动激活
- `SKILL.md` 总长建议 ≤ 5000 字；详细规则放 `references/`
- 文档统一用 Markdown，无 .docx / .txt / .py 转换件
- 业务内容版权归原公司所有；skill 结构部分按 MIT 协议开源
