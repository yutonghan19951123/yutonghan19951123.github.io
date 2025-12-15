# 视频文件设置说明

由于 GitHub 限制，大视频文件（>50MB）无法直接推送到仓库。请使用以下方案之一：

## 方案 1: 使用 GitHub Releases（推荐）

1. 在 GitHub 上创建 Release：
   - 访问：https://github.com/yutonghan19951123/yutonghan19951123.github.io/releases/new
   - 上传视频文件作为 Release 附件
   - 获取视频的直链 URL

2. 更新代码中的视频链接：
   - 编辑 `app/pages/phd-portfolio.vue`
   - 将视频路径替换为 GitHub Releases 的直链

## 方案 2: 使用云存储服务

可以使用以下服务之一：

- **Cloudinary** (免费): https://cloudinary.com
- **AWS S3** + CloudFront
- **Vercel Blob Storage**
- **其他 CDN 服务**

上传视频后，更新代码中的链接即可。

## 方案 3: 使用 Git LFS

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
