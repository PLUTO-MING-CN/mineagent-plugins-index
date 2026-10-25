# MineAgent Plugins Index

这是 MineAgent 插件市场的中心化索引仓库。客户端会拉取本仓库的 `index.json` 来展示插件。

## ⚠️ 安全声明
**本仓库仅做结构校验，不审核插件代码。** 安装第三方插件意味着在本机执行他人代码，风险自负。

## 📁 数据结构
`index.json` 格式如下：

```json
{
  "version": "1",
  "plugins": [
    {
      "name": "clock-sensor",
      "description": "整点报时插件",
      "author": "your-github-username",
      "repo": "your-github-username/mineagent-plugin-clock",
      "version": "1.0.0",
      "download_url": "https://github.com/your-github-username/.../clock.zip",
      "api_version": "1",
      "sha256": "a1b2c3d4e5f6...（64位十六进制）",
      "verified": false
    }
  ]
}
