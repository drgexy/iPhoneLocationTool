# iPhone Location Tool

这是一个在 macOS 上运行的本地小工具，用于你本人 iPhone 或 iOS 模拟器上的 App 开发、调试和测试定位。

它不会越狱，不会永久修改 iPhone 的真实 GPS 硬件，也不用于绕过地区限制、作弊或隐藏身份。真机模式依赖 iPhone 的开发者服务：需要开启开发者模式、连接并信任这台 Mac。

## 快速使用

1. 下载或克隆本项目，并打开项目文件夹
2. 第一次使用先双击 `install_dependencies.command`
3. 双击 `build_app.command` 生成 `iPhone Location Tool.app`
4. 以后可直接双击 `iPhone Location Tool.app`，也可以双击 `run.command`
5. 连接 iPhone，解锁，在手机上点“信任此电脑”
6. iPhone 设置里打开：隐私与安全性 > 开发者模式
7. 在工具里点击“刷新设备”，选择 iPhone，输入经纬度，点击“设置到此位置”
8. 测试结束后点击“结束模拟”或“清除模拟定位”

## 支持范围

- iOS 模拟器：使用 Xcode 自带的 `simctl location`，通常最稳定。
- iOS 17 及以上真机：使用 `pymobiledevice3 developer dvt simulate-location`。
- iOS 16 及以下真机：使用 `pymobiledevice3 developer simulate-location`。
- 工具会先尝试自动读取 iOS 版本，也可以在界面里手动选择定位通道。

## 真机使用前检查

- Mac 上安装了 Xcode。工具会优先识别 `/Applications/Xcode.app` 和 `/Applications/Xcode-beta.app`
- iPhone 已用 USB 数据线连接，已解锁
- iPhone 已信任这台 Mac
- iPhone 已开启开发者模式
- 没有 Xcode 或其他设备工具正在独占这台 iPhone

## 上传 GitHub 时建议包含

- `NativeApp/main.swift`
- `NativeApp/generate_icon.py`
- `NativeApp/Assets/AppIcon.icns`
- `NativeApp/Assets/AppLogo.png`
- `README.md`
- `requirements.txt`
- `install_dependencies.command`
- `build_app.command`
- `run.command`

不要上传 `.venv/`、`iPhone Location Tool.app/`、`.DS_Store`、`__pycache__/` 等本机生成文件。

## 常见问题

如果界面显示没有找到 `pymobiledevice3`，请先运行 `install_dependencies.command`。

如果设置真机定位失败，先重新插拔数据线、解锁手机，再点“刷新设备”。如果仍失败，重启 iPhone 后再试。

如果只是做 App 定位测试，优先用 iOS 模拟器，成功率和可控性最高。

如果要给 Xcode 使用，也可以点击“导出 GPX”，把生成的 `.gpx` 文件加入 Xcode 调试配置。
