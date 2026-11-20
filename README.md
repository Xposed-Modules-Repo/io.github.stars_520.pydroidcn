# Pydroid 3 界面汉化

Pydroid 3（`ru.iiec.pydroid3`）的中文界面模块，基于 LSPosed / Xposed。

本模块覆盖 Pydroid 3 的四条文字管线：Android 资源字符串、运行时 `TextView` 文本、
对话框与 Toast、以及 `assets/` 内的纯文本文件。词表从 APK 的 `resources.arsc`
逐条反查生成，实测版本 `8.4_arm64`（versionCode 1131）。

## 功能

- 594 条字符串资源汉化（菜单、设置项、按钮、提示、示例标题）
- 523 条运行时英文文本汉化（`setText` 直写的硬编码文案）
- 对话框标题/内容、Toast 提示
- `assets/` 内 `.txt/.json/.html/.kv/.cfg/.ini` 流内替换，不落盘

## 兼容

| 项 | 值 |
|---|---|
| Android | 7.0+（minSdk 24） |
| 框架 | LSPosed / EdXposed / 原版 Xposed（API 82+） |
| 目标 App | Pydroid 3 `ru.iiec.pydroid3` |

## 安装

1. 安装本模块 APK
2. 在 LSPosed 管理器中启用
3. 作用域勾选 **Pydroid 3**
4. 强制停止 Pydroid 3 后重新打开（必须冷启动）

## 构建

不依赖 Gradle，只需要系统 `aapt2`、`javac`、`d8`、`apksigner`：

```bash
bash build.sh
```

词表已包含在 `gen/` 中，无需重新反编译 APK 即可构建。

## 说明

- 只改界面显示文字，不修改任何功能逻辑
- 不触碰 Pydroid 的 Python 运行环境（`assets/finalpackage3_arm64.tar.xz`）
- `assets/` 的替换发生在 `AssetManager.open()` 返回的流上，APK 原文件不受影响

## 许可

MIT