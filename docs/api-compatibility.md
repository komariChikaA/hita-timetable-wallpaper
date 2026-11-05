# API 兼容性

结论：OH-MY-HITA 0.5.0 发布 API 6，提供原生课表外观服务；本插件已按该契约构建。

## 契约

- `HITA_API_VERSION = 6`
- `RuntimeUiService.CAP_TIMETABLE_APPEARANCE = "hita.ui.timetableAppearance"`
- `TimetableAppearanceService`：
  - `observe(): LiveData<TimetableAppearance>`
  - `update(settings)`
  - `importWallpaper(input: InputStream)`（阻塞，调用方负责关闭流）
  - `openWallpaper(): InputStream?`
  - `clearWallpaper()`
  - `reset()`

服务由宿主提供，插件只调用；APK 不应打包 `com.stupidtree.hita.api.*`。

## 宿主侧入口

- 原生样式面板在 `RuntimeUiService.isAvailable(CAP_TIMETABLE_APPEARANCE)` 为真时显示“壁纸与外观”，点击 `open(...)`；失败时保留原生面板。
- 市场中“我的插件”卡片仍是备用入口。

## 参考

- 宿主 master `759fb87`
- API AAR SHA-256 `44c20f04f155cbeb598aae4dd372079430d90386bdbfc0c95de41f09193f06ba`
