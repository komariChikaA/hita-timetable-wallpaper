# HITA 课表壁纸与样式

基于 [hita-plugin-template](https://github.com/kajimi16/hita-plugin-template) 的独立插件仓库，调整 OH-MY-HITA 原有课表的壁纸、课程卡片不透明度、背景模糊、暗色遮罩和风格预设。

**面向 OH-MY-HITA 0.5.0 / API 6。** 插件通过 `TimetableAppearanceService` 写入宿主外观状态，由宿主原生课表渲染；不是独立 App，也不打包宿主 API。

支持系统选图/清除/重置、卡片不透明度 0–100%、模糊 0–30、遮罩 0–80%，以及清晰/柔光/磨砂/夜幕预设。设置保存于宿主，不保存另一份课程数据，不上传图片。设置插件关闭或卸载后保留偏好，可恢复默认；清除内置课表数据时清理壁纸。

## 构建

```bash
./gradlew :ui-plugin:assembleRelease
```

产物：`ui-plugin/build/outputs/apk/release/ui-plugin-release-unsigned.apk`。直接依赖 `libs/api-release.aar` 等官方 AAR，仓库不再保留接口副本；发布前确认 `libs` 为 API 6。

## 发布流程

1. 宿主 0.5.0（API 6）装机自测：安装、打开设置、选图、重启、清除、卸载后重装。
2. 推送验证过的源码并递增版本号。
3. 在 [社区仓库](https://github.com/kajimi16/hita-community-plugins/issues/new/choose) 提交“插件发布请求”Issue。
4. 维护者运行 Publish Plugin，CI 构建、校验并更新 `dist/` 与 `registry/index.json`。
5. 刷新市场安装验证。

发布字段与当前状态见 [发布状态](docs/publishing.md)。
