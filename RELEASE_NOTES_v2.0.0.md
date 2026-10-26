# 地球Online iOS · v2.0.0 发布说明

## 版本定位

暂停端。本端最新基线为 v1.0.5（封板能力快照）。v2.0.0 在本仓库为占位，不单独发版；仅在未来安全修复时启用发布流水线。

## 亮点

无（本端暂停维护）。v1.0.5 封板能力：SwiftUI + SwiftData、WebDAV 同步（URLSession 自建）、高德可选集成（默认 MapKit）、App Intents、灵动岛实时活动、小组件扩展。

## 破坏性变更

无。

## 升级指引

暂停维护，不提供升级路径。已侧载用户停留在 v1.0.5（SideStore 自签名）；如需迁移数据，请用应用内 WebDAV 备份导出后导入其他活跃端。

## 已知问题

- 本端冻结，不再接收功能更新。
- 未签名 ipa 需 SideStore 续签（7 天），详见 `Docs/` 安装指南。

## 完整变更

后续由 git-cliff 基于 Conventional Commits 自动生成并维护于 `CHANGELOG.md`。
