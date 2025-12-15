# Deployment Guide

部署指南 | Deployment Guide

## 概述 (Overview)

BAGUA 是一个纯前端静态网站，可以部署到任何静态托管服务。
BAGUA is a pure frontend static website that can be deployed to any static hosting service.

## 快速部署 (Quick Deployment)

### 1. Netlify (推荐 / Recommended)

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/bajibaji/BAGUA)

**步骤 (Steps):**
1. 点击上方按钮 (Click the button above)
2. 连接您的 GitHub 账户 (Connect your GitHub account)
3. 授权访问 (Authorize access)
4. 等待自动部署完成 (Wait for automatic deployment)

**配置文件** (`netlify.toml`):
```toml
[build]
  publish = "."
  command = "echo 'No build required'"

[[redirects]]
  from = "/*"
  to = "/index.html"
  status = 200
```

### 2. Vercel

**步骤 (Steps):**
1. 安装 Vercel CLI (Install Vercel CLI)
   ```bash
   npm i -g vercel
   ```
2. 在项目目录运行 (Run in project directory)
   ```bash
   vercel
   ```
3. 按照提示完成部署 (Follow prompts to complete deployment)

**配置文件** (`vercel.json`):
```json
{
  "routes": [
    { "handle": "filesystem" },
    { "src": "/(.*)", "dest": "/index.html" }
  ]
}
```

### 3. GitHub Pages

**步骤 (Steps):**
1. 进入仓库设置 (Go to repository Settings)
2. 找到 Pages 选项 (Find Pages option)
3. 选择主分支 (Select main branch)
4. 保存并等待部署 (Save and wait for deployment)

网站将在 `https://username.github.io/BAGUA` 访问
Site will be available at `https://username.github.io/BAGUA`

### 4. Firebase Hosting

**步骤 (Steps):**
1. 安装 Firebase CLI (Install Firebase CLI)
   ```bash
   npm install -g firebase-tools
   ```
2. 登录 Firebase (Login to Firebase)
   ```bash
   firebase login
   ```
3. 初始化项目 (Initialize project)
   ```bash
   firebase init hosting
   ```
4. 部署 (Deploy)
   ```bash
   firebase deploy
   ```

**配置文件** (`firebase.json`):
```json
{
  "hosting": {
    "public": ".",
    "ignore": [
      "firebase.json",
      "**/.*",
      "**/node_modules/**"
    ],
    "rewrites": [
      {
        "source": "**",
        "destination": "/index.html"
      }
    ]
  }
}
```

### 5. AWS S3 + CloudFront

**步骤 (Steps):**
1. 创建 S3 存储桶 (Create S3 bucket)
2. 启用静态网站托管 (Enable static website hosting)
3. 上传文件 (Upload files)
   ```bash
   aws s3 sync . s3://your-bucket-name --exclude ".git/*"
   ```
4. 配置 CloudFront (Optional, for HTTPS and CDN)

## 本地测试 (Local Testing)

### 方法 1: Python HTTP Server
```bash
python3 -m http.server 8080
```

### 方法 2: Node.js HTTP Server
```bash
npx http-server -p 8080 -o
```

### 方法 3: Live Server (VS Code)
1. 安装 Live Server 扩展 (Install Live Server extension)
2. 右键点击 index.html (Right-click index.html)
3. 选择 "Open with Live Server" (Select "Open with Live Server")

访问 http://localhost:8080
Visit http://localhost:8080

## 环境变量 (Environment Variables)

本项目不需要环境变量。
This project does not require environment variables.

## 性能优化 (Performance Optimization)

### CDN 资源 (CDN Resources)
项目使用以下 CDN：
The project uses the following CDNs:
- Google Fonts
- jsDelivr (GSAP)
- Tailwind CSS CDN

### 缓存策略 (Caching Strategy)
建议配置以下缓存头：
Recommended cache headers:

```
# HTML files
Cache-Control: no-cache

# JavaScript and CSS
Cache-Control: public, max-age=31536000

# Images
Cache-Control: public, max-age=31536000

# JSON data
Cache-Control: public, max-age=86400
```

### Gzip 压缩 (Gzip Compression)
确保服务器启用 Gzip 压缩：
Ensure server has Gzip compression enabled:
- HTML
- CSS
- JavaScript
- JSON

## 安全配置 (Security Configuration)

### HTTPS
**始终使用 HTTPS！**
**Always use HTTPS!**

### 安全头 (Security Headers)
```
Content-Security-Policy: default-src 'self'; script-src 'self' 'unsafe-inline' https://cdn.jsdelivr.net https://cdn.tailwindcss.com https://fonts.googleapis.com; style-src 'self' 'unsafe-inline' https://fonts.googleapis.com; font-src 'self' https://fonts.gstatic.com; img-src 'self' data:;
X-Frame-Options: SAMEORIGIN
X-Content-Type-Options: nosniff
Referrer-Policy: strict-origin-when-cross-origin
Permissions-Policy: geolocation=(), microphone=(), camera=()
```

## 监控和分析 (Monitoring & Analytics)

如需添加分析工具，建议：
If you need to add analytics tools, we recommend:
- Google Analytics (可选 / Optional)
- Plausible Analytics (隐私友好 / Privacy-friendly)
- Cloudflare Web Analytics (免费 / Free)

## 故障排除 (Troubleshooting)

### 问题：页面空白 (Issue: Blank Page)
- 检查浏览器控制台错误 (Check browser console for errors)
- 确认所有 CDN 资源可访问 (Verify all CDN resources are accessible)
- 检查 JavaScript 文件是否正确加载 (Check if JavaScript files load correctly)

### 问题：样式丢失 (Issue: Missing Styles)
- 确认 Tailwind CSS CDN 可访问 (Verify Tailwind CSS CDN is accessible)
- 检查 Google Fonts 是否加载 (Check if Google Fonts load)
- 清除浏览器缓存 (Clear browser cache)

### 问题：功能不工作 (Issue: Features Not Working)
- 确认 GSAP 库已加载 (Verify GSAP library is loaded)
- 检查数据文件是否存在 (Check if data files exist)
- 查看浏览器控制台错误 (Check browser console for errors)

## 更新部署 (Update Deployment)

大多数平台支持自动部署：
Most platforms support automatic deployment:
1. 推送代码到 GitHub (Push code to GitHub)
2. 平台自动检测更改 (Platform detects changes automatically)
3. 触发新部署 (Triggers new deployment)

## 自定义域名 (Custom Domain)

各平台配置方法：
Configuration for each platform:
- **Netlify**: Settings → Domain Management
- **Vercel**: Settings → Domains
- **GitHub Pages**: Settings → Pages → Custom domain
- **Firebase**: firebase.json → hosting → site

## 支持 (Support)

如有部署问题，请：
For deployment issues, please:
1. 查看平台文档 (Check platform documentation)
2. 在 GitHub 创建 issue (Create issue on GitHub)
3. 联系平台支持 (Contact platform support)

## 相关链接 (Related Links)

- [Netlify Documentation](https://docs.netlify.com/)
- [Vercel Documentation](https://vercel.com/docs)
- [GitHub Pages Documentation](https://docs.github.com/pages)
- [Firebase Hosting Documentation](https://firebase.google.com/docs/hosting)
- [AWS S3 Static Website Hosting](https://docs.aws.amazon.com/AmazonS3/latest/userguide/WebsiteHosting.html)
