# 🚀 我的 Scoop 软件源 (Scoop Bucket)

这是一个用于存放我个人常用软件安装配置（Manifest）的 Scoop 软件源。使用 Scoop 可以方便地在 Windows 环境下进行一键安装、更新和管理。

当前已收录的软件：
*   **图吧工具箱 (tbtool)**：最纯净的硬件检测与系统测试工具合集。
*   **InputTip (inputtip)**：规则驱动的输入法状态（中/英/大写锁定）管理器。

---

## 🛠️ 使用方法

### 1. 添加此软件源

您可以选择直接通过本地路径添加，或者在将其推送到远程 Git 仓库（如 GitHub / Gitee）后通过 URL 添加。

**方式 A：通过本地文件路径添加（推荐本地开发使用）**
```powershell
scoop bucket add my-bucket "c:\Users\maorila\Documents\scoop-bucket"
```

**方式 B：通过 Git 仓库地址添加（推送到 GitHub/Gitee 后使用）**
```powershell
scoop bucket add my-bucket "您的仓库Git地址"
```

---

### 2. 安装软件

添加成功后，您可以使用以下命令安装此软件源中的软件：

```powershell
# 安装图吧工具箱
scoop install my-bucket/tbtool

# 安装 InputTip
scoop install my-bucket/inputtip
```

---

## ➕ 如何在此仓库中添加新软件？

若您未来需要添加其他软件，请按照以下步骤操作：

### 第一步：在 `bucket` 目录下创建 JSON 文件
在 `bucket` 文件夹中新建一个以软件名命名的 `.json` 文件（建议全小写，如 `my-app.json`）。

### 第二步：编写软件清单内容 (JSON Schema)
将以下模板复制到新建的 JSON 文件中，并根据您的软件修改对应属性：

```json
{
    "version": "1.0.0",
    "description": "软件的一句话中文介绍",
    "homepage": "软件的官方主页链接",
    "license": "软件授权协议类型 (例如: MIT, GPL-3.0-only, Freeware, Proprietary)",
    "url": "软件的直接下载链接 (必须是点击即可直接下载的直链)",
    "hash": "计算出的软件下载文件 SHA-256 哈希值",
    "bin": "安装后需要加入系统环境变量的运行程序文件名 (例如: myapp.exe)",
    "shortcuts": [
        [
            "myapp.exe",
            "开始菜单中的快捷方式名称"
        ]
    ],
    "persist": [
        "config.json",
        "data"
    ]
}
```

#### 💡 核心字段说明：
1.  **url**: 软件的直链地址。
    *   若是 `.zip` 或 `.7z` 压缩包，Scoop 会自动解压。
    *   如果是自解压可执行程序（例如 `.exe`），可以在 URL 结尾添加 `#/dl.7z`，告诉 Scoop 将其作为压缩包解压。
2.  **hash**: 下载文件的哈希校验码。支持 `SHA-256`（推荐）和 `MD5`（需加 `md5:` 前缀）。
3.  **shortcuts**: 自动在 Windows 开始菜单中创建快捷方式。格式为 `["可执行程序路径", "快捷方式展示名称"]`。
4.  **persist**: 将软件的配置文件或数据目录持久化，防止软件更新时数据丢失。可以使用文件名或目录名。

---

### 第三步：计算文件的哈希值 (Hash)
Scoop 必须使用哈希值来保证下载文件的安全和完整性。您可以通过 PowerShell 计算下载文件的 SHA-256 哈希：

```powershell
Get-FileHash "C:\路径\下载的软件文件.zip" -Algorithm SHA256
```
运行后，将输出的 `Hash` 值（长字符串，全大写或全小写皆可）填入 JSON 的 `"hash"` 字段中。如果官网只提供了 MD5 校验码，您也可以填入 `"hash": "md5:您的MD5值"`。

---

### 第四步：本地测试安装
在提交修改前，可以通过本地路径快速测试 Manifest 是否编写正确：

```powershell
# 1. 刷新 Scoop 本地缓存
scoop update

# 2. 尝试测试安装您的新软件
scoop install my-bucket/my-app
```

---

### 第五步：使用 Git 提交并推送
测试无误后，使用符合规范的 Git 提交信息提交更改：

```bash
# 暂存更改
git add .

# 提交（使用中文 Conventional Commits 规范）
git commit -m "feat: 新增 my-app 软件清单"
```
