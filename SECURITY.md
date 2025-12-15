# Security Policy

## Supported Versions

当前支持的版本 (Currently supported versions):

| Version | Supported          |
| ------- | ------------------ |
| 0.2.x   | :white_check_mark: |
| < 0.2   | :x:                |

## Reporting a Vulnerability

如果您发现了安全漏洞，请通过以下方式报告：
If you discover a security vulnerability, please report it via:

1. **不要** 公开提交 issue (Do NOT create a public issue)
2. 发送邮件至项目维护者 (Email the project maintainer)
3. 或通过 GitHub Security Advisory (Or use GitHub Security Advisory)

我们会尽快响应并处理安全问题。
We will respond and address security issues as quickly as possible.

## Security Best Practices

本项目遵循以下安全最佳实践：
This project follows these security best practices:

### 前端安全 (Frontend Security)

- ✅ 使用 HTTPS 部署 (Deploy with HTTPS)
- ✅ 避免存储敏感信息 (Avoid storing sensitive information)
- ✅ 使用 CDN 的 SRI (Subresource Integrity)
- ✅ 输入验证和清理 (Input validation and sanitization)

### 依赖安全 (Dependency Security)

- 定期检查依赖更新 (Regularly check for dependency updates)
- 使用可信的 CDN 源 (Use trusted CDN sources)
- 监控安全公告 (Monitor security advisories)

### 数据隐私 (Data Privacy)

- 本应用不收集用户数据 (This app does not collect user data)
- 所有计算在客户端完成 (All calculations are performed client-side)
- 不使用追踪或分析工具 (No tracking or analytics tools used)

## Content Security Policy

建议在部署时添加以下 CSP 头：
It is recommended to add the following CSP header when deploying:

```
Content-Security-Policy: default-src 'self'; script-src 'self' 'unsafe-inline' https://cdn.jsdelivr.net https://cdn.tailwindcss.com https://fonts.googleapis.com; style-src 'self' 'unsafe-inline' https://fonts.googleapis.com; font-src 'self' https://fonts.gstatic.com; img-src 'self' data:;
```

## Updates

安全更新将及时发布在：
Security updates will be published at:

- GitHub Security Advisories
- Release Notes

感谢您帮助保持项目安全！🔒
Thank you for helping keep the project secure! 🔒
