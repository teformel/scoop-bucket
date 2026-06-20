# 🚀 我的 Scoop 软件源 (Scoop Bucket)

这是一个用于存放我个人常用软件安装配置（Manifest）的 Scoop 软件源，同时也是一份详尽的 Scoop 仓库维护与开发全能教程。使用 Scoop 可以方便地在 Windows 环境下进行一键安装、更新和管理。

---

## 📁 当前收录软件

### 公共开源软件 (提供自动更新)
*   **图吧工具箱 (tbtool)**：最纯净的硬件检测与系统测试工具合集。
*   **InputTip (inputtip)**：输入法状态（中/英/大写锁定）提示管理器。
*   **TrafficMonitor (trafficmonitor)**：任务栏网速与硬件状态监控工具。
*   **noMeiryoUI (nomeiryoui)**：修改 Windows 系统各部分字体的快捷工具。
*   **LiteMonitor (litemonitor)**：轻量级桌面硬件监控。
*   **Czkawka (czkawka)**：多功能重复文件与空文件夹清理工具。
*   **Ventoy (ventoy)**：新一代多合一系统 U 盘启动制作工具。
*   **KeyCastOW (keycastow)**：键盘按键可视化回显工具。
*   **Aria2-Manager (aria2manager)**：Aria2 命令行下载器的后台挂载与管理工具。
*   **Blender 3.6 LTS (blender36)**：开源三维动画制作软件 3.6 长期支持版。
*   **ChoEazyCopy (choeazycopy-cn)**：微软 Robocopy 经典命令行复制工具的中文 GUI 包装。
*   **DesktopInfo (desktopinfo)**：将系统硬件监控信息直接呈现在桌面壁纸上的工具。
*   **小熊猫 Dev-C++ (devcpp-redpanda)**：快速、轻量的 C/C++ IDE 便携版。
*   **Dism++ (dismplusplus)**：实用的 Windows 系统底层组件优化与精简清理工具。
*   **FFmpeg (ffmpeg)**：经典的多媒体音视频处理库 (Gyan.dev Git 版)。
*   **GDA (gda)**：GJoy Dex Analyzer 安卓 APK 反编译与逆向分析工具。
*   **Godot 3 (godot3)**：开源、轻量级的 2D/3D 游戏引擎 v3 稳定维护版。
*   **LiteLoaderQQNT (liteloaderqqnt)**：新版 QQNT 客户端插件加载器。
*   **WifiInfoView (wifiinfoview)**：多维度无线 WiFi 网络热点扫描查看器。
*   **N_m3u8DL-CLI (n-m3u8dl-cli)**：经典好用的 m3u8 命令行视频下载器 (自动依赖安装 ffmpeg)。
*   **WinFi (winfi)**：专业的无线 WiFi 现场勘测与无线信号诊断分析仪 (WinFi Pro 免费版)。

### 本地私有/官方动态软件 (预留占位符清单)
*   **APK助手 (apk-helper)**：方便的本地 APK 快速安装器 (主页已关联 GitHub 源码库)。
*   **Alice in Cradle (alice-in-cradle)**：同人 2D 动作游戏 (已填入正版游戏最新客户端直链接口)。
*   **PCL 启动器 (pcl2)**：国内备受欢迎的《我的世界》第三方游戏启动器模板。
*   **Cheat Engine (cheat-engine)**：开源的内存修改与调试工具 (由于官方 7.4 绿色版直链已下线，预留本地私有占位符)。

---

## 📌 待收录软件 (因缺乏稳定公开直链暂未添加)

以下免安装便携软件由于官网没有提供免登录的稳定下载直链，目前暂未制作 Scoop 清单。后续如找到直链可能会重新收录：
*   **MyDockFinder** (仿 Mac 桌面美化工具)
*   **搞机工具箱** (晨钟酱玩机激活工具)
*   **几何画板** (经典的函数几何作图软件)
*   **妹调教日记** (同人视觉小说游戏)
*   **手写模拟器** (仿人手写字迹排版生成器)
*   **软媒魔方** (第三方绿色去广告便携优化版)

---
## 🛠️ 快速使用指南

### 1. 添加此软件源
您可以直接通过本地路径添加（便于测试），或者推送到远程仓库后通过 URL 添加：

*   **方式 A：通过本地文件路径添加（推荐本地开发使用）**
    ```powershell
    scoop bucket add my-bucket "file:///c:/Users/maorila/Documents/scoop-bucket"
    ```
*   **方式 B：通过远程 Git 仓库添加（推送到 GitHub / Gitee 后使用）**
    ```powershell
    scoop bucket add my-bucket https://github.com/teformel/scoop-bucket.git
    ```

### 2. 安装软件
添加成功后，您可以使用以下命令直接安装此软件源中的软件：
```powershell
# 安装图吧工具箱
scoop install my-bucket/tbtool

# 安装 InputTip
scoop install my-bucket/inputtip
```

---

## 📖 Scoop 仓库制作与维护全能教程

制作 Scoop 仓库非常简单：其本质就是一个 Git 仓库，按约定格式在 `bucket` 文件夹内存放软件清单（JSON 文件）即可，无需复杂的服务端配置。

### 一、标准仓库目录结构
Scoop 有固定的目录约定，所有软件清单必须放在 `bucket` 子目录下才能被系统正确识别：

```plaintext
scoop-bucket/             # 仓库根目录
├── bucket/               # 【必填】存放所有软件清单（.json 文件，如 tbtool.json）
│   ├── tbtool.json
│   ├── inputtip.json
│   └── ...
├── scripts/              # 【可选】存放自定义安装/卸载脚本
├── README.md             # 【可选】仓库说明文档（本文件）
└── LICENSE               # 【可选】开源协议
```

---

### 二、编写软件清单 (Manifest)
每个软件对应一个 `.json` 清单文件，**文件名即为软件名**（规范为全小写、用连字符分隔，例如 `my-app.json`）。

#### 1. 标准清单模板示例
以下是一个包含分架构、持久化、快捷方式和自动更新的完整 Manifest 示例：

```json
{
    "version": "1.2.0",
    "description": "轻量级命令行示例工具",
    "homepage": "https://github.com/yourname/demo-tool",
    "license": "MIT",
    "architecture": {
        "64bit": {
            "url": "https://github.com/yourname/demo-tool/releases/download/v1.2.0/demo-tool-v1.2.0-win-amd64.zip",
            "hash": "sha256:1234567890abcdef1234567890abcdef1234567890abcdef1234567890abcdef"
        },
        "32bit": {
            "url": "https://github.com/yourname/demo-tool/releases/download/v1.2.0/demo-tool-v1.2.0-win-386.zip",
            "hash": "sha256:fedcba0987654321fedcba0987654321fedcba0987654321fedcba0987654321"
        }
    },
    "extract_dir": "demo-tool-v1.2.0-win-amd64",
    "bin": [
        ["demo-tool.exe", "demo"]
    ],
    "shortcuts": [
        ["demo-tool.exe", "Demo Tool"]
    ],
    "persist": "config",
    "checkver": {
        "github": "yourname/demo-tool"
    },
    "autoupdate": {
        "architecture": {
            "64bit": {
                "url": "https://github.com/yourname/demo-tool/releases/download/v$version/demo-tool-v$version-win-amd64.zip"
            },
            "32bit": {
                "url": "https://github.com/yourname/demo-tool/releases/download/v$version/demo-tool-v$version-win-386.zip"
            }
        }
    }
}
```

#### 2. 核心字段详细对照表

| 字段 | 作用 |
| :--- | :--- |
| `version` | 软件版本号，与下载包版本严格对应 |
| `description` | 软件的一句话中文介绍，描述软件功能 |
| `homepage` | 软件的官方网站或项目仓库主页 |
| `license` | 软件的开源协议类型 (例如: `MIT`, `GPL-3.0-only`, `Freeware`, `Proprietary`) |
| `url` | 安装包直链地址。如果是 `.exe` 等单文件，可追加 `#/dl.7z` 以支持解压 |
| `hash` | 安装包哈希值。默认推荐 `sha256:`，也可使用 `md5:`（格式如 `md5:xxx`） |
| `extract_dir` | 提取压缩包内的子目录，将该目录内容拉取到软件根目录，解决压缩包外层嵌套问题 |
| `bin` | 添加到系统 `PATH` 的可执行文件。可写成 `[["原程序.exe", "命令别名"]]` |
| `shortcuts` | 创建到 Windows 开始菜单的快捷方式，格式为 `["可执行文件相对路径", "快捷方式名称"]` |
| `persist` | 持久化配置。软件升级时自动保留指定的数据文件夹或配置文件，防止数据丢失 |
| `architecture` | 分架构适配，可分别定义 `64bit` 与 `32bit` 的 `url` 和 `hash` |
| `checkver` | 配置如何自动检查更新（支持 Github Releases 等） |
| `autoupdate` | 配置自动升级时如何替换 `url` 和计算 `hash` |

---

### 三、辅助开发与校验命令

#### 1. 快速获取文件哈希 (Hash)
无需手动下载计算，在命令行中运行以下命令即可直接获取哈希校验值：
```powershell
# 语法
scoop checksum <下载链接>

# 示例
scoop checksum https://github.com/yourname/demo-tool/releases/download/v1.2.0/demo-tool.zip
```
这会输出类似于 `sha256:xxxxxx` 的长字符串，直接复制到 `hash` 字段即可。

#### 2. 校验清单语法格式
在将 Manifest 文件加入 bucket 前，可利用 Scoop 工具检查 JSON 的语法规范，以避免潜在的编写错误：
```powershell
scoop lint bucket/demo-tool.json
```
如果命令返回没有输出任何错误信息，则表示清单格式规范合规。

---

### 四、本地调试与测试

无需先推送到远程仓库，您可以直接在本地进行调试：

1.  **将本地仓库添加为 Scoop Bucket**：
    ```powershell
    scoop bucket add my-bucket "file:///c:/Users/maorila/Documents/scoop-bucket"
    ```
2.  **验证软件是否可被搜索**：
    ```powershell
    scoop search demo-tool
    ```
3.  **安装并运行测试**：
    ```powershell
    scoop install demo-tool
    ```
    *若能成功拉取、解压并能在控制台/快捷方式正常运行，则代表清单文件开发正确。*

---

### 五、配置自动更新 (强烈推荐)

手动维护版本号和哈希非常低效。添加 `checkver` 和 `autoupdate` 字段后，我们可以使用 Scoop 自带脚本批量检测并升级清单。

#### 1. 自动检测配置模板 (以 GitHub Releases 为例)
```json
"checkver": {
    "github": "你的用户名/项目名"
},
"autoupdate": {
    "url": "https://github.com/你的用户名/项目名/releases/download/v$version/app-v$version.zip"
}
```

#### 2. 执行自动更新命令
```powershell
# 1. 检查并更新单个软件清单
scoop checkver demo-tool -u

# 2. 批量检查并更新整个本地 Bucket 的所有软件
scoop checkver * -u
```
*提示：执行后，脚本会自动抓取 GitHub/官网 最新版本，拉取文件并重新计算 SHA-256，然后直接写入您本地的 JSON 清单中。*

---

### 六、常用进阶技巧

1.  **安装前后脚本 (pre_install / post_install)**：
    支持在 Manifest 中写入 PowerShell 命令数组，在安装前/后执行特定的操作。
    *   例如：在安装后复制持久化文件、注册系统服务或修改配置文件编码。
    ```json
    "post_install": [
        "Copy-Item \"$dir\\config.default.json\" \"$dir\\config.json\" -Force"
    ]
    ```
2.  **国内源加速优化**：
    如果在国内使用，可将 `url` 替换为国内代理镜像（如 `https://ghproxy.com/` 镜像加速地址），提高拉取稳定性。

---

### 💡 最佳实践原则
*   **优先绿色版**：优先收录便携版/免安装软件，符合 Scoop 不侵入、不污染注册表的理念。
*   **命名规范**：文件名必须全小写，遇到多个单词用短横线 `-` 连接。
*   **信息完整**：尽量写全 `homepage` 和 `license`，保持清单规范可查。
