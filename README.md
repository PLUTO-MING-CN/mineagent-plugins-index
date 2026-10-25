# MineAgent Plugins Index

这是 [MineAgent](https://github.com/PLUTO-MING-CN/mineagent) 插件市场的官方中心化索引仓库。MineAgent 客户端会从本仓库拉取 `index.json` 来展示可用的插件列表。

## ⚠️ 安全声明

**本仓库仅做结构校验，不审核插件代码。**
安装第三方插件意味着在本机以完整权限运行他人的 Python 代码。请务必确认你信任插件的作者。如果你选择了安装，风险由你自己承担。

## 📁 数据结构

根目录下的 `index.json` 维护了所有可用的插件。格式如下：

```json
{
  "version": "1",
  "plugins": [
    {
      "name": "clock-sensor",
      "description": "整点报时插件，提供一个时钟事件。",
      "author": "your-github-username",
      "repo": "your-github-username/mineagent-plugin-clock",
      "version": "1.0.0",
      "download_url": "https://github.com/your-github-username/mineagent-plugin-clock/releases/download/v1.0.0/clock.zip",
      "api_version": "1",
      "sha256": "a1b2c3d4e5f6...（64位十六进制）",
      "verified": false
    }
  ]
}
```

### 字段说明

| 字段 | 类型 | 要求 |
| :--- | :--- | :--- |
| `name` | String | 插件唯一标识。1-64 个字符，仅限**小写**字母、数字及 `. _ -`。 |
| `description` | String | 插件简介。最多 500 字。 |
| `author` | String | 作者名（GitHub 用户名即可）。 |
| `repo` | String | 插件源码仓库路径，格式 `owner/repo`。 |
| `version` | String | 插件版本号（与你的 Release Tag 对应，如 `1.0.0`）。 |
| `download_url` | String | 插件 `.zip` 包的直链。**必须是 `https://`**，且托管在 GitHub 或其镜像上。 |
| `api_version`| String | 插件兼容的 MineAgent API 版本。当前仅支持 `"1"`。 |
| `sha256` | String | 插件 `.zip` 包的 SHA256 哈希值（64位十六进制）。用于保证下载安全。 |
| `verified` | Boolean| 是否已验证。普通提交请填 `false`。 |

## 🚀 如何提交插件

1. **打包插件**：确保插件根目录包含 `manifest.json` 和入口文件，打包为 `.zip`。
2. **发布 Release**：在你的 GitHub 仓库中创建 Release，上传 `.zip` 并获取下载直链。
3. **计算 SHA256**：
   - **Windows (PowerShell)**: `Get-FileHash .\your-plugin.zip -Algorithm SHA256`
   - **macOS / Linux**: `shasum -a 256 your-plugin.zip`
4. **Fork 本仓库**。
5. 在 `index.json` 的 `plugins` 数组中添加你的插件信息。
6. **提交 Pull Request (PR)**。
7. PR 会自动触发 GitHub Actions 进行格式校验（需管理员配置 Workflow）。校验通过后，管理员会进行合并。

## 🛠️ 本地校验（可选）

如果你在本地 clone 了 [MineAgent 主仓库](https://github.com/PLUTO-MING-CN/mineagent)，可以在提交前跑一下校验：

```bash
python -m backend.core.plugin_index --check index.json
```

如果没有报错并显示 `索引校验通过`，说明格式完全正确。
