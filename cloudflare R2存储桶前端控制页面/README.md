# ☁️ R2 多账户管理器 · 纯前端缓存控制台

一个功能完备的 Cloudflare R2 存储桶管理工具，完全运行在浏览器中。支持多账户切换、本地缓存搜索（不消耗 LIST 请求）、大文件分片上传、文件夹递归勾选、Markdown/PDF/Excel 在线预览编辑。

## ✨ 核心功能

- **多账户支持**：保存/切换多个 R2 账户配置（Account ID / Access Key / Secret Key / 桶名 / 自定义域名）
- **零 LIST 搜索**：基于 IndexedDB 本地缓存，搜索文件名不消耗 R2 操作费
- **递归文件夹勾选**：勾选文件夹自动选中其下所有文件
- **大文件上传**：支持并发分片上传，自动重试，可上传文件夹
- **增强预览/编辑**：
  - 图片 / PDF / Excel 在线预览
  - Markdown 渲染（代码高亮 + 行号 + 复制按钮）
  - TXT / MD / DOCX 在线编辑保存
- **容量指示器**：基于本地缓存估算已用空间（10 GB 免费额度可视化）[注]：需要点击`同步缓存`
- **右键菜单**：复制 URL / 下载 / 预览 / 编辑 / 删除
- **导出 CSV**：将勾选文件的 URL 导出为表格

## 🚀 使用方法

1. 用浏览器打开此 HTML 文件
2. 点击「隐藏配置」展开配置栏，填入 R2 账户信息
3. 点击「连接」测试连通性，再点击「同步缓存」将文件列表存入本地
4. 之后即可使用搜索、上传、下载、预览等功能

## 🧰 技术栈

- AWS SDK for JavaScript (S3 兼容)
- IndexedDB (idb) – 本地缓存
- PDF.js / SheetJS (XLSX) / Mammoth.js – 文档预览
- Marked + Highlight.js – Markdown 渲染
- Font Awesome – 图标库

## ⚠️ 注意事项

- Secret Key 仅保存在浏览器 localStorage，请勿在公共电脑使用

- 「同步缓存」会调用 LIST 操作，建议仅在必要时执行

- 自定义域名需已在 R2 中绑定并配置 CORS

  ```
  CORS配置为：
  [
    {
      "AllowedOrigins": [
        "*"
      ],
      "AllowedMethods": [
        "GET",
        "PUT",
        "POST",
        "DELETE",
        "HEAD"
      ],
      "AllowedHeaders": [
        "*"
      ],
      "ExposeHeaders": [
        "ETag"
      ]
    }
  ]
  ```

  

## 📄 许可

MIT