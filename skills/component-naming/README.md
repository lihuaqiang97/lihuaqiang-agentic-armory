# 组件命名规范（component-naming）

> 作者：**lihuaqiang**（李华强）  
> 版本：v1.0  
> 最后更新：2026-06-13

## 背景

在 Flutter/Dart 项目开发中，组件（Package/Module）的命名是架构设计中容易被忽视但极其重要的一环。错误的命名不仅违反 Dart 官方 lint 规则，还会导致团队协作时的理解成本上升。

本规范由 **lihuaqiang** 在 APP 项目的架构实践中总结提炼，融合了：

- **Dart 官方规范**：`package_names` lint 规则、Effective Dart 设计原则
- **Flutter 社区最佳实践**：Feature-first 拆分、Clean Architecture + DDD 分层
- **工程实战经验**：三层组件化架构下的命名隔离（组件名 vs 路由路径 vs 类名）

## 适用场景

- 创建新业务组件（`feature_*`）、基础组件（`core_*`）、共享组件（`shared_*`）
- 编写 `pubspec.yaml` 的 `name` 字段
- 团队代码规范中关于命名的统一约定
- 新成员 onboarding 时的架构入门指南

## 核心原则

1. **snake_case 是铁律**：所有 Dart package 名必须小写 + 下划线，没有例外
2. **前缀即身份**：`feature_`/`core_`/`shared_` 一眼识别组件类型
3. **业务优先**：组件名从业务域提取（如 `account`），而非技术实现（如 `webview`）
4. **命名空间隔离**：组件名、路由路径、类名各有其规范，互不干扰

## 速查

| 场景 | 命名 | 示例 |
|------|------|------|
| 新业务组件 | `feature_` + 业务域 | `feature_account` |
| 新基础组件 | `core_` + 技术域 | `core_network` |
| 类名 | `UpperCamelCase` | `UserModePage` |
| 文件名 | `snake_case` | `account_page.dart` |
| 路由路径 | `kebab-case` | `/user-profile` |

完整规范详见 `SKILL.md`。
