# GitHub Pages 部署指南

本项目已配置为支持 GitHub Pages 部署。

## 部署步骤

### 1. 更新配置

在部署前，请确保更新以下文件中的 URL：

- `astro.config.ts` 第 27 行：已设置为 `https://LonelyBattle.github.io`
- `src/site.config.ts` 第 120-121 行：已设置为 `https://LonelyBattle.github.io/`

### 2. 启用 GitHub Pages

1. 进入你的 GitHub 仓库
2. 点击 "Settings" 标签
3. 在左侧菜单中找到 "Pages"
4. 在 "Source" 部分选择 "GitHub Actions"
5. 保存设置

### 3. 推送代码

将代码推送到 `main` 分支，GitHub Actions 会自动构建并部署你的网站。

```bash
git add .
git commit -m "Configure for GitHub Pages deployment"
git push origin main
```

### 4. 查看部署状态

1. 进入你的仓库的 "Actions" 标签
2. 查看 "Deploy to GitHub Pages" 工作流的状态
3. 部署成功后，你的网站将在 `https://LonelyBattle.github.io` 可用

## 本地测试

在部署前，你可以本地测试静态构建：

```bash
npm run build:static
npm run preview
```

## 注意事项

- 确保你的仓库是公开的（除非你有 GitHub Pro 账户）
- 如果使用自定义域名，请更新 `astro.config.ts` 中的 `site` 配置
- 如果部署到子路径（如 `username.github.io/repository-name`），请取消注释并修改 `base` 配置

## 故障排除

如果部署失败，请检查：

1. GitHub Actions 日志中的错误信息
2. 确保所有依赖都已正确安装
3. 检查 `astro.config.ts` 中的配置是否正确
4. 确保仓库有正确的权限设置
5. 如果出现 "No lockfile found" 错误，确保 `bun.lock` 文件已提交到仓库

## 常见问题

### 包管理器错误
如果遇到包管理器相关的错误，确保：
- `bun.lock` 文件已提交到仓库
- GitHub Actions 工作流中正确配置了 `package-manager: bun@latest`
