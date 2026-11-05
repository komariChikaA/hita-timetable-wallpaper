# 公开 API 兼容性复核（2026-11-05）

结论：存在打开内置课表样式面板的接口，但公开 API 尚不能让外部插件设置原生课表壁纸、卡片透明度和背景模糊。保持原生课表的壁纸插件继续等待接口支持，未提交发布请求。

## 核对范围

- [宿主 master](https://github.com/kajimi16/OH-MY-HITA/tree/9ebd58dd0dfeb85320847dd221254a60abdab99d)：`9ebd58dd0dfeb85320847dd221254a60abdab99d`。
- [社区仓库 master](https://github.com/kajimi16/hita-community-plugins/tree/19e81454f02a30d8c7c34fa12d1a0075dc389262)：`19e81454f02a30d8c7c34fa12d1a0075dc389262`。
- [模板 main](https://github.com/kajimi16/hita-plugin-template/tree/213f6aa718a81d3c044a8b3a23ac29a4e844730f)：`213f6aa718a81d3c044a8b3a23ac29a4e844730f`。
- 拉取并检索宿主所有公开分支的 API 源码，包括较新的 `feat/plugin-guide-polish`；检查社区与模板实际 API AAR 的所有 29 个顶层类，以及 model/component AAR 是否包含课表外观契约。
- 社区与模板 API AAR 完全一致，SHA-256：`bcc6cba6bbfd9b17f4d60b0ab0dbd71cc7fa5b1ace2e4e0cac68e7a4e8784258`；`javap` 确认 `HITA_API_VERSION = 5`。

## 已有能力与缺口

| 项目 | 当前能力 |
|---|---|
| `TimetableUiService.openStylePanel(activity)` | 打开内置样式面板，无设置参数、读写返回值或注册扩展入口 |
| `ThemeController.setNightMode(night)` | 设置应用夜间模式 |
| `TimetableService` | 课程数据读写、课程颜色等；没有壁纸、模糊和卡片透明度接口 |
| 内部 `TimetableStyleSheet.cardOpacity` | 默认 95；内部 Repository 未监听透明度设置，外部契约没有暴露此对象 |
| 原生壁纸 / 模糊 | 当前原生课表没有对应的加载与渲染入口 |

源码证据：[样式面板契约](https://github.com/kajimi16/OH-MY-HITA/blob/9ebd58dd0dfeb85320847dd221254a60abdab99d/api/src/main/java/com/stupidtree/hita/api/TimetableUiService.kt)、[实际面板实现](https://github.com/kajimi16/OH-MY-HITA/blob/9ebd58dd0dfeb85320847dd221254a60abdab99d/plugin-hita/src/main/java/com/stupidtree/hitax/plugin/TimetableUiImpl.kt)、[样式对象](https://github.com/kajimi16/OH-MY-HITA/blob/9ebd58dd0dfeb85320847dd221254a60abdab99d/plugin-hita/src/main/java/com/stupidtree/hitax/ui/main/timetable/TimetableStyleSheet.kt)、[样式仓库](https://github.com/kajimi16/OH-MY-HITA/blob/9ebd58dd0dfeb85320847dd221254a60abdab99d/plugin-hita/src/main/java/com/stupidtree/hitax/data/repository/TimetableStyleRepository.kt)。

[外观接口草案 PR #1](https://github.com/kajimi16/OH-MY-HITA/pull/1) 复核时仍 open、未合并。API 版本号本身不是唯一判断依据；上述结论来自 AAR 方法签名、宿主实现和公开分支源码。

## 后续恢复

如果维护者提供新的提交、分支或 AAR，重新核对实际外观契约，并适配当前草稿。待原生课表确实消费这些设置、完成构建和装机自测后，再按社区 Issue 流程请求发布。

本轮只复核 API，没有改动运行时代码，没有重新执行设备测试。此前基于配套接口草案的测试结果不代表正式宿主兼容。
