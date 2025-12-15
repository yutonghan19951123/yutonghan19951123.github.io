# 视频文件设置说明

由于 GitHub 限制，大视频文件（>50MB）无法直接推送到仓库。请使用以下方案：

## 方案: 使用 Git LFS

如果需要将视频保留在仓库中：

```bash
# 安装 Git LFS
brew install git-lfs  # macOS
# 或访问 https://git-lfs.github.com

# 初始化 Git LFS
git lfs install

# 追踪视频文件
git lfs track "public/img/projects/**/*.mp4"

# 添加 .gitattributes
git add .gitattributes

# 重新添加视频文件
git add public/img/projects/3d_pillar/demo.mp4
git add public/img/projects/ai-agent/demo.mp4

# 提交
git commit -m "Add videos using Git LFS"
git push
```

## 当前状态

视频文件已添加到 `.gitignore`，不会被 Git 追踪。
请在完成视频上传后，更新 `app/pages/phd-portfolio.vue` 中的视频路径。
