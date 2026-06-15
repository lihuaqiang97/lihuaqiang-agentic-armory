---
name: component-naming
description: Dart/Flutter 组件命名最佳实践规范。在创建新业务组件（feature）、基础组件（core）、共享组件（shared）时使用；在编写 pubspec.yaml 的 name 字段时使用；当用户询问包命名、组件命名、目录命名等命名规范问题时使用。覆盖 Dart 官方 snake_case 强制规则、Feature/Core/Shared 前缀约定、以及组件名与路由路径的命名空间隔离。
---

# 组件命名规范

## Overview

Dart/Flutter 组件命名规范，基于 Dart 官方 `package_names` lint 规则和项目约定。

## Dart 官方硬性约束

Package 名称（`pubspec.yaml` 的 `name` 字段、组件目录名）必须满足：

- 格式：全部小写 + 下划线分隔（`snake_case`）
- 允许字符：仅限 `[a-z0-9_]`
- 首字符：不能是数字
- 禁止：大写字母、连字符 `-`、空格、特殊字符、Dart 保留字

## 命名规范速查表

| 命名对象 | 规范 | 示例 |
|----------|------|------|
| Package / 组件目录名 | `snake_case` | `feature_user_profile`、`core_network` |
| Feature 前缀 | `feature_` + 业务域名词 | `feature_account`、`feature_order` |
| Core 前缀 | `core_` + 技术域名词 | `core_storage`、`core_network` |
| Shared 前缀 | `shared_` + 层级名 | `shared_domain`、`shared_data` |
| Dart 类名 | `UpperCamelCase` | `UserProfilePage`、`OrderDetailCard` |
| Dart 变量/方法名 | `lowerCamelCase` | `userName`、`submitOrder()` |
| Dart 文件名 | `snake_case` | `user_profile_page.dart` |
| 文件夹名 | `snake_case` | `domain/`、`data/`、`presentation/` |
| 路由路径 | `kebab-case` | `/user-profile`、`/order-detail` |

## Feature 组件命名决策树

```
1. 业务功能还是技术能力？
   ├─ 业务功能 → feature_ 前缀
   └─ 技术能力 → core_ 前缀

2. 用一句话描述职责，提取核心业务域名词
   → 例："用户个人主页的展示页" → user_profile

3. 组合：feature_user_profile
   → pubspec name / 目录名 / barrel file 统一使用此名称
```

## 常见错误示例

| 错误 | 正确 | 原因 |
|------|------|------|
| `userMode` | `user_mode` | camelCase 违反 `snake_case` |
| `user-mode` | `user_mode` | 连字符不允许出现在 package 名中 |
| `usermode` | `user_mode` | 单词粘连，可读性差 |
| `Feature_User_Mode` | `feature_user_mode` | 全大写/中划线不允许 |

## 组件名 vs 路由路径

组件名和路由路径是独立命名空间：

| 概念 | 规范 | 示例 |
|------|------|------|
| 组件目录 | `snake_case` | `lib/features/feature_user_profile/` |
| pubspec name | `snake_case` | `feature_user_profile` |
| 路由路径 | `kebab-case` | `/user-profile` |
| 页面类名 | `UpperCamelCase` | `UserProfilePage` |
| 页面文件 | `snake_case` | `user_profile_page.dart` |
