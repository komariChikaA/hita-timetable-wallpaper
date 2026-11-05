# HITA 课表壁纸与样式

基于 [hita-plugin-template](https://github.com/kajimi16/hita-plugin-template) 的独立插件仓库，调整 OH-MY-HITA 原有课表的壁纸、课程卡片不透明度、背景模糊、暗色遮罩和风格预设。

**开发草稿，未发布。等待维护者支持原生课表外观接口，当前 API 5 正式宿主无法使用。**

支持系统选图/清除/重置、卡片不透明度 0–100%、模糊 0–30、遮罩 0–80%，以及清晰/柔光/磨砂/夜幕预设。设置保存于宿主，不保存另一份课程数据，不上传图片。设置插件关闭或卸载后保留偏好，可恢复默认；清除内置课表数据时清理壁纸。

## 构建

```bash
./gradlew :ui-plugin:assembleRelease
```

产物 ui-plugin/build/outputs/apk/release/ui-plugin-release-unsigned.apk，由兼容宿主加载，不是独立 App。wallpaper-contract 是 compileOnly 的接口草案，APK 不携带宿主 API 或运行时。正式发布前按维护者最终接口调整。

## 发布流程

1. 等待正式宿主支持外观服务，使用最终 API AAR/协议重新构建并装机自测。
2. 推送验证过的源码和版本号。
3. 在 [社区仓库](https://github.com/kajimi16/hita-community-plugins/issues/new/choose) 提交“插件发布请求”Issue。
4. 维护者运行 Publish Plugin，CI 构建、校验并更新 dist/ 和 registry/index.json。
5. 刷新市场安装；更新时必须递增 version。

当前不提交发布请求，不把不兼容包加入市场。宿主 [接口方案 #1](https://github.com/kajimi16/OH-MY-HITA/pull/1) 仅供维护者讨论外观能力，发布不依赖向社区提交源码 PR。

发布字段与等待事项见 [发布状态](docs/publishing.md)。
