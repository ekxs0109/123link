# 123pan秒传JSON生成器（夸克网盘/天翼云盘）

一键生成 123 云盘（123pan）秒传 JSON 的浏览器脚本，支持夸克网盘、天翼云盘。

## ✨ 特性

- 📦 支持夸克网盘（个人文件、分享链接）
- 📦 支持天翼云盘（个人文件、分享链接）
- 📁 支持文件夹批量获取
- 🎯 自动生成秒传 JSON 格式
- 🔐 支持加密分享链接
- 💰 完全免费
- 🚀 一键复制或下载 JSON

## 📦 安装

### 1. 安装脚本管理器

首先需要在浏览器中安装脚本管理器扩展：

- **Tampermonkey**（推荐）：[Chrome](https://chrome.google.com/webstore/detail/tampermonkey/dhdgffkkebhmkfjojejmpbldmpobfkfo) | [Firefox](https://addons.mozilla.org/firefox/addon/tampermonkey/) | [Edge](https://microsoftedge.microsoft.com/addons/detail/tampermonkey/iikmkjmpaadaobahmlepeloendndfphd)
- **Violentmonkey**：[Chrome](https://chrome.google.com/webstore/detail/violentmonkey/jinjaccalgkegednnccohejagnlnfdag) | [Firefox](https://addons.mozilla.org/firefox/addon/violentmonkey/)

### 2. 安装脚本

点击下方链接安装脚本：

**[点击安装脚本](https://greasyfork.org/scripts/脚本ID)**

或者直接访问 Greasyfork 搜索 "123pan秒传JSON生成器"

## 📖 使用说明

### 夸克网盘 - 个人文件

1. 访问 [夸克网盘](https://pan.quark.cn/)
2. 勾选需要生成秒传的文件或文件夹
3. 点击页面上的 **"生成JSON"** 按钮
4. 等待扫描完成后，选择 **复制** 或 **下载** JSON

### 夸克网盘 - 分享链接

1. 打开任意夸克网盘分享链接（如：https://pan.quark.cn/s/xxxxxx）
2. **首次使用需要设置 Cookie**（脚本会自动提示）
   - 按 `F12` 打开开发者工具
   - 切换到 `Network` 标签
   - 刷新页面，找到任意请求
   - 在请求头（Request Headers）中找到 `Cookie` 值
   - 复制完整的 Cookie 字符串（必须包含：`__puus`、`__pus`、`ctoken` 等）
3. 点击 **"生成JSON"** 按钮
4. 等待扫描完成后，选择 **复制** 或 **下载** JSON

> **注意**：Cookie 会被缓存，下次使用无需重新输入，除非失效

### 天翼云盘 - 个人文件

1. 访问 [天翼云盘](https://cloud.189.cn/web/main/)
2. 勾选需要生成秒传的文件或文件夹
3. 点击页面上的 **"生成JSON"** 按钮
4. 等待扫描完成后，选择 **复制** 或 **下载** JSON

### 天翼云盘 - 分享链接

1. 打开任意天翼云盘分享链接（如：https://cloud.189.cn/t/xxxxxx）
2. 如有提取码，确保已输入提取码（脚本会自动读取）
3. 勾选需要生成秒传的文件或文件夹
4. 点击页面上的 **"生成JSON"** 按钮
5. 等待扫描完成后，选择 **复制** 或 **下载** JSON

## 🔗 配合使用

推荐配合 [123FastLink](https://github.com/Bao-qing/123FastLink) 使用：

1. 使用本脚本生成秒传 JSON
2. 使用 123FastLink 客户端导入秒传文件
3. 快速转存到你的 123 云盘

或者配合 Cloudflare Worker 版本使用：

- 在线服务：[https://123.kkit.app](https://123.kkit.app)
- 项目地址：[123fastlink-cf](https://github.com/ekxs0109/123fastlink-cf)

## 🛠️ 技术细节

### 支持的功能

- ✅ 夸克网盘个人文件和文件夹
- ✅ 夸克网盘分享链接（含密码保护）
- ✅ 天翼云盘个人文件和文件夹
- ✅ 天翼云盘分享链接（含提取码）
- ✅ 自动递归扫描文件夹
- ✅ 批量获取文件 MD5
- ✅ 自动生成标准 123pan 秒传格式

### 生成的 JSON 格式

```json
{
  "scriptVersion": "3.0.3",
  "exportVersion": "1.0",
  "usesBase62EtagsInExport": false,
  "commonPath": "",
  "files": [
    {
      "path": "文件名.ext",
      "etag": "md5哈希值",
      "size": 文件大小（字节）
    }
  ],
  "totalFilesCount": 文件总数,
  "totalSize": 总大小（字节）
}
```

## ❓ 常见问题

### Q1: 夸克分享链接提示 "请先登录网盘" 或 Cookie 失效？

**A**: 需要更新 Cookie：
1. 点击错误提示框中的 "修改Cookie" 按钮
2. 或刷新页面后重新点击生成 JSON
3. 按照提示重新获取并粘贴 Cookie

### Q2: 天翼云盘分享链接只能看到根目录文件？

**A**: 这是天翼云盘的限制，分享链接的子文件夹可能需要登录才能访问。建议：
- 直接勾选根目录的所有文件
- 或者使用个人文件功能（需登录天翼云盘后操作）

### Q3: 扫描过程中卡住或失败？

**A**: 可能的原因：
- 网络连接不稳定，刷新后重试
- Cookie 失效（夸克网盘），需要更新 Cookie
- 文件数量过多，请耐心等待
- 部分文件无法获取 MD5，会自动跳过

### Q4: 生成的 JSON 如何使用？

**A**: 使用 [123FastLink](https://github.com/Bao-qing/123FastLink) 客户端：
1. 下载并安装 123FastLink
2. 登录你的 123 云盘账号
3. 导入生成的 JSON 文件
4. 选择目标文件夹，开始秒传

## 🔒 隐私说明

- 本脚本完全在本地浏览器运行
- 不会上传或收集任何数据
- Cookie 仅存储在本地浏览器
- 所有请求均直接与云盘服务器通信

## 📝 更新日志

### v1.0.0 (2025-01-10)
- ✨ 初始版本发布
- ✅ 支持夸克网盘个人文件和分享链接
- ✅ 支持天翼云盘个人文件和分享链接
- ✅ 自动递归扫描文件夹
- ✅ 批量获取文件 MD5

## 📄 许可证

Apache License 2.0

## 🤝 贡献

欢迎提交 Issue 和 Pull Request！

## 🔗 相关项目

- [123FastLink](https://github.com/Bao-qing/123FastLink) - 123 云盘秒传客户端
- [123fastlink-cf](https://github.com/ekxs0109/123fastlink-cf) - Cloudflare Worker 版本

## 👤 作者

**ekxs**

---

如果觉得有用，请给个 ⭐️ Star 支持一下！
