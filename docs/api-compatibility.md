# 公开 API 兼容性复核（2026-11-06）

结论：OH-MY-HITA 0.5.0 已提供原生课表外观接口 `TimetableAppearanceService`（API 6）。本插件的 `wallpaper-contract` 与宿主 `api/TimetableAppearanceService.kt` 内容一致，插件可按最终契约编译。尚未完成装机自测，因此未提交发布请求。

## 核对范围

- 宿主 `master` / `v0.5.0`：`759fb87`；外观接口由 [PR #1](https://github.com/kajimi16/OH-MY-HITA/pull/1) 合入，维护者合并提交 `aa2e555`。
- `api/src/main/java/com/stupidtree/hita/api/Plugin.kt`：`HITA_API_VERSION = 6`。
- 宿主 `api/src/main/java/com/stupidtree/hita/api/TimetableAppearanceService.kt` 与本仓库 `wallpaper-contract` 同源；仅行尾不同（CRLF/LF）。
- 宿主已实现 `TimetableAppearanceStore`、`TimetableWallpaperLayer`，并在 `TimetableFragment`、`TimeTableBlockView`、`TimetableWeekView`、`LeftLabelView` 中消费外观设置。

## 能力对照

| 能力 | API 6 状态 |
|---|---|
| 壁纸选择 / 清除 / 恢复默认 | `importWallpaper` / `clearWallpaper` / `reset` |
| 卡片不透明度 0–100 | `TimetableAppearance.cardOpacity` |
| 背景模糊 0–30 | `TimetableAppearance.blurRadius` |
| 暗色遮罩 0–80 | `TimetableAppearance.scrimOpacity` |
| 设置观察与持久化 | `observe()`；由宿主私有偏好保存，关闭/卸载设置插件后保留 |

## 后续

1. 在 Android 8.0+ 真机/模拟器完成选图、取消、坏图、超限、透明度/模糊、重启恢复、深浅色和旧系统模糊回退测试。
2. 更新 [发布状态](publishing.md) 的验收记录。
3. 按社区模板提交“插件发布请求”Issue；维护者 CI 构建并更新 dist/registry。

本轮完成的是 API 与构建核对，未执行设备测试，不代表已经发布。

## 历史复核（2026-11-05）

当时公开 API 仍为 5：`TimetableUiService.openStylePanel(activity)` 只能打开内置样式面板，`ThemeController` 只有 `setNightMode`，没有壁纸、模糊、遮罩和卡片透明度读写契约。该结论已被 API 6 取代。
