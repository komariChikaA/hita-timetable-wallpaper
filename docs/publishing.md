# 发布状态

Status: 待提交发布请求（代码已适配 OH-MY-HITA 0.5.0 / API 6）。

| 字段 | 值 |
|---|---|
| repo | komariChikaA/hita-timetable-wallpaper |
| module | :ui-plugin |
| kind | ui |
| id | io.github.komarichikaa.hita.wallpaper |
| version | 0.1.0（首次发布；之后每次更新递增） |
| entryClass | io.github.komarichikaa.hita.wallpaper.WallpaperPlugin |
| minHostApi | 6 |
| capability | hita.ui.timetableAppearance |

## 已验证

- 使用官方 API 6 AAR 构建通过，APK 不包含 `com.stupidtree.hita.api.*`。
- 官方 0.5.0 上通过市场源安装，设置页可打开。
- 选图后提示“壁纸已保存”，返回课表可见壁纸。
- 宿主样式面板在检测到该能力时显示“壁纸与外观”入口；未安装/停用时隐藏。
- 卸载/停用行为与设置保留由宿主 `TimetableAppearanceService` 负责。

## 发布前检查

- `libs/*.aar` 为 API 6，不提交 `wallpaper-contract` 副本。
- `./gradlew publishMarket` 成功生成 `market/`。
- README、plugin.json、发布 Issue 的 id/version/module 一致。
- 版本递增后再提交发布请求。
