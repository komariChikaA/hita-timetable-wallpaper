# 发布状态

Status: API 6 已由 OH-MY-HITA 0.5.0 提供；插件可构建，待装机自测，未发布。

| 字段 | 值 |
|---|---|
| repo | komariChikaA/hita-timetable-wallpaper |
| module | :ui-plugin |
| kind | ui |
| id | io.github.komarichikaa.hita.wallpaper |
| version | 0.1.0（首次发布前，之后更新递增） |
| entryClass | io.github.komarichikaa.hita.wallpaper.WallpaperPlugin |
| minHostApi | 6 |

## 已完成

- 宿主 API 6 已合入 `kajimi16/OH-MY-HITA` master，随 v0.5.0 发布（PR #1，合并提交 `aa2e555`）。
- `wallpaper-contract` 与宿主 `api/TimetableAppearanceService.kt` 内容一致，仅行尾不同。
- `:ui-plugin:assembleRelease` 构建通过（本地，2026-11-06）。
- 既有 API 6 草案验证：宿主与插件构建成功，69 项单元测试通过，42 个外部符号无缺失；3 项图片存储设备测试已编译，未执行。

## 待完成

- Android 8.0+ 真机/模拟器装机自测：选图/取消/坏图/超限、透明度/模糊、重启恢复、深浅色、Android 6–11 模糊回退、清除/卸载边界。
- 自测通过后按需更新 version 并推送源码。
- 按社区“插件发布请求”Issue 流程提交，由维护者 CI 构建并更新 dist/registry。

当前不提交发布请求，不把未验收包加入市场。
