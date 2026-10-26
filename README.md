# 地球Online · iOS

![Platform](https://img.shields.io/badge/platform-iOS-SwiftUI-000000) ![Version](https://img.shields.io/badge/version-v2.0.0-lightgrey) ![License](https://img.shields.io/badge/license-MIT-green)

同名应用的 iOS 端，SwiftUI + SwiftData。

## 当前状态

暂停维护，基线 v1.0.5。v2.0.0 在本仓库为封板时的能力快照占位，不单独发版；仅在未来安全修复时启用发布流水线（`release.yml`，既有 `ios-build.yml` 云端构建未签名 ipa 的流水线保留不删）。

## 技术栈（v1.0.5 封板时的能力快照）

- SwiftUI + SwiftData
- WebDAV 同步（URLSession 自建最小实现，零 SwiftPM 第三方依赖，覆盖 PROPFIND / GET / PUT / MKCOL）
- 高德 SDK 可选集成（默认 MapKit；`EO_MAP_BACKEND=amap` 切换）
- App Intents / 灵动岛实时活动 / 小组件扩展
- 最低系统 iOS 17

## 跨端契约

四端共用同一份数据契约 `earth-online-backup.json`。一条硬规则：导入严格按主键合并（`recordId == id` 命中即更新，未命中才插入），永不整包覆盖。完整契约见 Web 仓库 [docs/contract.md](https://github.com/IllNFree/EarthOnline-Web/blob/main/docs/contract.md)。

## 快速开始

暂停维护，不提供新构建指引。

## 仓库导航

- Web（PWA）：https://github.com/IllNFree/EarthOnline-Web
- Android：https://github.com/IllNFree/EarthOnline-Android
- Desktop（Windows）：https://github.com/IllNFree/EarthOnline-Desktop

## 许可证

[MIT](LICENSE)

---

## 工程结构与本地构建

| 目录 / 文件 | 作用 |
| --- | --- |
| `project.yml` | xcodegen 工程描述（主 App + 小组件扩展） |
| `xcconfig/` | 编译设置：Common / Debug / Release；Secrets.local.xcconfig 存本地高德 Key（不入库） |
| `Sources/App/` | Views / Model(SwiftData) / Data(BackupService 按主键合并) / Net(WebDavClient) / Services / Domain |
| `Sources/Shared/` | 主 App 与小组件共用快照结构 |
| `.github/workflows/` | `ios-build.yml`（云端构建未签名 ipa）+ `release.yml`（git-cliff 发版） |

本地构建需 Mac：

```bash
brew install xcodegen
xcodegen generate --spec project.yml
open EarthOnline.xcodeproj
```

无 Mac 时推送到 GitHub 即触发 Actions，产物为未签名 ipa，用 SideStore 自签名安装（见 `Docs/`）。仓库地址已统一为 `IllNFree/EarthOnline-iOS`。
