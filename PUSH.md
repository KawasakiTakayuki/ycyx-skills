# 推送到 GitHub 指南

## 步骤 1：在 GitHub 网页创建仓库

1. 打开 https://github.com/new
2. 填写：
   - **Repository name**: `ycyx-skills`
   - **Owner**: `KawasakiTakayuki`（会自动补全你的账号）
   - **Description**: 玉柴研学文旅新媒体文案 AI 写作 Skill 集合
   - **Visibility**: Public（推荐，便于 skill 被发现）
   - **不要勾选** "Initialize this repository with a README"（我们已经有本地仓库）
3. 点击 **Create repository**

## 步骤 2：在终端推送本地仓库

创建完成后，**回到本终端**，我会自动检测到并执行以下命令：

```bash
cd /Volumes/Samsung980pro/AI/ycyx-artical
git remote add origin git@github.com:KawasakiTakayuki/ycyx-skills.git
git push -u origin main
```

## 备选：HTTPS 方式（如果你没配 SSH key）

```bash
cd /Volumes/Samsung980pro/AI/ycyx-artical
git remote add origin https://github.com/KawasakiTakayuki/ycyx-skills.git
git push -u origin main
```

> 首次 HTTPS 推送会要求输入 GitHub 用户名和 Personal Access Token（密码）。
> 旧版密码已停用，请到 https://github.com/settings/tokens 生成 PAT。

## 推送完成后

- 仓库地址：https://github.com/KawasakiTakayuki/ycyx-skills
- 默认分支：`main`
- 首次 commit：`feat: 初始化 ycyx-artical skill`

## 后续添加新 skill

```bash
cd /Volumes/Samsung980pro/AI/ycyx-skills
# 例如把另一个 skill 放进 ycyx-foo/ 目录
git add ycyx-foo/
git commit -m "feat: 新增 ycyx-foo skill"
git push
```

## 注意事项

- 当前仓库根目录仅包含 `ycyx-artical/` 一个 skill。如果未来要加多个 skill，每个 skill 一个子目录，便于独立管理。
- 当前 commit 使用的邮箱是 `KawasakiTakayuki@users.noreply.github.com`（GitHub 自动生成的匿名邮箱，避免泄露真实邮箱）。如需改为你自己的邮箱，请在推送前修改：
  ```bash
  cd /Volumes/Samsung980pro/AI/ycyx-artical
  git -c user.email="your@email.com" commit --amend --reset-author --no-edit
  ```
