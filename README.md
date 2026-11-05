# HITA 课表壁纸与样式

基于 [hita-plugin-template](https://github.com/kajimi16/hita-plugin-template) 的独立插件仓库，调整 OH-MY-HITA 原有课表的壁纸、课程卡片不透明度、背景模糊、暗色遮罩和风格预设。

**API 6 已随 OH-MY-HITA 0.5.0 提供；插件可构建，待装机自测后发布。**

支持系统选图/清除/重置、卡片不透明度 0–100%、模糊 0–30、遮罩 0–80%，以及清晰/柔光/磨砂/夜幕预设。设置保存于宿主，不保存另一份课程数据，不上传图片。设置插件关闭或卸载后保留偏好，可恢复默认；清除内置课表数据时清理壁纸。

## 构建

```bash
./gradlew :ui-plugin:assembleRelease
```

产物 ui-plugin/build/outputs/apk/release/ui-plugin-release-unsigned.apk，由兼容宿主加载，不是独立 App。wallpaper-contract 是 compileOnly 的最终 API 6 契约，与宿主 `TimetableAppearanceService.kt` 内容一致；APK 不携带宿主 API 或运行时。

## 发布流程

1. 在 Android 8.0+ 真机/模拟器完成装机自测。
2. 推送验证过的源码和版本号。
3. 在 [社区仓库](https://github.com/kajimi16/hita-community-plugins/issues/new/choose) 提交“插件发布请求”Issue。
4. 维护者运行 Publish Plugin，CI 构建、校验并更新 dist/ 和 registry/index.json。
5. 刷新市场安装；更新时必须递增 version。

当前不提交发布请求，不把未验收包加入市场。宿主接口已随 0.5.0 发布，发布不依赖向社区提交源码 PR。

发布字段与等待事项见 [发布状态](docs/publishing.md)。
