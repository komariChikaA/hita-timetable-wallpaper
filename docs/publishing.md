# 发布状态

Status: 等待原生课表外观接口支持；未发布。

| 字段 | 草案 |
|---|---|
| repo | komariChikaA/hita-timetable-wallpaper |
| module | :ui-plugin |
| kind | ui |
| id | io.github.komarichikaa.hita.wallpaper |
| version | 0.1.0（首次发布前，之后更新递增） |
| entryClass | io.github.komarichikaa.hita.wallpaper.WallpaperPlugin |
| minHostApi | 接口草案为 6，按维护者最终确认结果填写 |

等待正式外观接口、最终契约、图片选择/透明度/重启/深浅色/旧系统模糊装机验收。满足后再提交发布请求 Issue，不提前发布。

既有 API 6 草案验证：宿主与插件构建成功，69 项单元测试通过，42 个外部符号无缺失；3 项图片存储设备测试已编译，未执行。这些结果不表示当前正式版支持。

2026-11-05 复核：公开 API 5 提供 `openStylePanel()` 面板入口，仍未提供原生壁纸/透明度/模糊读写能力。详见 [API 兼容性复核](api-compatibility.md)。
