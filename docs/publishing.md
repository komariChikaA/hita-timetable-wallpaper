# 发布状态

Status: 代码已适配 OH-MY-HITA 0.5.0 / API 6；基础装机路径已验证，待完整边界自测后提交发布请求。

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

## 已完成

- 宿主 API 6 已随 OH-MY-HITA v0.5.0 发布。
- 使用官方 API 6 AAR 构建通过，APK 不包含 `com.stupidtree.hita.api.*`。
- 官方 0.5.0 上通过本地市场源安装，设置页可打开。
- 选图后提示“壁纸已保存”，返回课表可见壁纸。
- 宿主样式面板在检测到该能力时显示“壁纸与外观”入口；未安装/停用时隐藏。

## 待完成

- Android 8.0+ 真机/模拟器边界自测：取消选图、坏图/超限、透明度/模糊、重启恢复、深浅色、旧系统模糊回退、清除/卸载。
- 自测通过后按需递增 version 并推送源码。
- 按社区“插件发布请求”Issue 流程提交，由维护者 CI 构建并更新 dist/registry。

## 发布前检查

- `libs/*.aar` 为 API 6，不提交 `wallpaper-contract` 副本。
- `./gradlew publishMarket` 成功生成 `market/`。
- README、plugin.json、发布 Issue 的 id/version/module 一致。
