# 喵墨网站部署文件

本目录包含部署到 `hujiaofenwritingcat.top` 所需的所有文件。

## 📁 文件结构

```
website-deploy/
├── index.html              # 官网首页
├── user-agreement.html     # 用户协议页面
├── privacy-policy.html     # 隐私政策页面
├── auto-renew-agreement.html # 自动续费服务协议页面
├── stellaai/               # 星恋AI 官网与法务页面（复用同域名）
│   ├── index.html          # 星恋AI 官网首页
│   ├── user-agreement.html # 星恋AI 用户协议
│   ├── privacy-policy.html # 星恋AI 隐私政策
│   ├── auto-renew-agreement.html # 星恋AI 自动续费服务协议
│   ├── en/                 # English legal pages (Stella AI)
│   │   ├── user-agreement.html
│   │   ├── privacy-policy.html
│   │   └── auto-renew-agreement.html
│   ├── es/                 # Spanish legal pages
│   ├── fr/                 # French legal pages
│   ├── ja/                 # Japanese legal pages
│   ├── ko/                 # Korean legal pages
│   ├── images/             # Logo / favicon
│   └── stellaai_show/      # App 展示截图
└── README.md               # 本文件
```

## 🚀 快速部署

### 方法一：FTP/SFTP 上传（推荐）

1. **使用 FTP 客户端**（如 FileZilla、WinSCP）
2. **连接到您的服务器**
3. **上传所有文件**到网站根目录（通常是 `public_html/` 或 `www/`）
4. **确保文件权限正确**：
   - HTML 文件：644
   - 目录：755

### 方法二：使用命令行（SSH）

```bash
# 使用 scp 上传
scp -r website-deploy/* user@your-server:/path/to/website/

# 或使用 rsync
rsync -avz website-deploy/ user@your-server:/path/to/website/
```

## ✅ 部署后检查

1. 访问 `https://hujiaofenwritingcat.top` 确认首页正常
2. 检查链接：
   - 用户协议：`https://hujiaofenwritingcat.top/user-agreement.html`
   - 隐私政策：`https://hujiaofenwritingcat.top/privacy-policy.html`
   - 自动续费服务协议：`https://hujiaofenwritingcat.top/auto-renew-agreement.html`
   - 星恋AI 官网：`https://hujiaofenwritingcat.top/stellaai/`
   - 星恋AI 各语言法务页：见下方「星恋AI 法务页地址」，逐个打开确认
3. 确认图片正常显示
4. 测试移动端访问

## 🌐 星恋AI 营销网站地址

| 语言 | 网址 | 对应文件 |
|------|------|----------|
| 中文 | https://hujiaofenwritingcat.top/stellaai/ | `stellaai/index.html` |
| English | https://hujiaofenwritingcat.top/stellaai/en/ | `stellaai/en/index.html` |

- 两个首页右上角均有「中文 / English」切换
- App Store Connect 中「营销网址（Marketing URL）」与「技术支持网址（Support URL）」：简体中文商品页填中文首页，其它语言商品页填英文首页（首页已含产品简介、下载链接、支持邮箱与协议链接）

## 🌐 星恋AI 法务页地址

中文为**中国大陆版**（放在 `stellaai/` 根目录）；其它语言为**国际版**（放在 `stellaai/{语言代码}/`），以英文版为准，其它语言译本仅供参考。App 内按当前界面语言加载对应版本（本地 `assets/legal/`，内容与这里保持一致）。

| 语言 | 用户协议 | 隐私政策 | 自动续费服务协议 |
|------|----------|----------|------------------|
| 简体中文（中国大陆版） | https://hujiaofenwritingcat.top/stellaai/user-agreement.html | https://hujiaofenwritingcat.top/stellaai/privacy-policy.html | https://hujiaofenwritingcat.top/stellaai/auto-renew-agreement.html |
| English（国际版，以此为准） | https://hujiaofenwritingcat.top/stellaai/en/user-agreement.html | https://hujiaofenwritingcat.top/stellaai/en/privacy-policy.html | https://hujiaofenwritingcat.top/stellaai/en/auto-renew-agreement.html |
| Español | https://hujiaofenwritingcat.top/stellaai/es/user-agreement.html | https://hujiaofenwritingcat.top/stellaai/es/privacy-policy.html | https://hujiaofenwritingcat.top/stellaai/es/auto-renew-agreement.html |
| Français | https://hujiaofenwritingcat.top/stellaai/fr/user-agreement.html | https://hujiaofenwritingcat.top/stellaai/fr/privacy-policy.html | https://hujiaofenwritingcat.top/stellaai/fr/auto-renew-agreement.html |
| 日本語 | https://hujiaofenwritingcat.top/stellaai/ja/user-agreement.html | https://hujiaofenwritingcat.top/stellaai/ja/privacy-policy.html | https://hujiaofenwritingcat.top/stellaai/ja/auto-renew-agreement.html |
| 한국어 | https://hujiaofenwritingcat.top/stellaai/ko/user-agreement.html | https://hujiaofenwritingcat.top/stellaai/ko/privacy-policy.html | https://hujiaofenwritingcat.top/stellaai/ko/auto-renew-agreement.html |

App Store Connect 中各语言商品页的「隐私政策网址」填对应语言的隐私政策地址；没有单独译本的语言填英文版。

修改法务页时，`website-deploy/stellaai/` 与 App 仓库 `stella_ai/assets/legal/` 两处需同步更新。

## 📝 注意事项

- 确保域名 DNS 已正确解析到服务器
- 如果使用 HTTPS，确保 SSL 证书已配置
- 检查服务器是否支持 `.html` 文件扩展名（通常默认支持）

## 🔧 故障排除

**问题：404 错误**
- 检查文件是否上传到正确目录
- 确认首页文件名为 `index.html`

**问题：图片无法显示**
- 检查 `images/` 目录是否已上传
- 确认图片路径为相对路径 `images/screenshot1.png`

**问题：链接无法访问**
- 确认文件权限正确
- 检查服务器配置是否允许访问 `.html` 文件
