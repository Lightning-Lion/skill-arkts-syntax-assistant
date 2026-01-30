---
name: harmony-dev
description: |-
  ArkTS 开发助手，用于 HarmonyOS/OpenHarmony 应用开发端到端开发
  工作流（代码-构建-部署-测试-调试循环）。
license: MIT
tags:
  - arkts
  - harmonyos
  - typescript
  - migration
  - development
  - syntax
---

# ArkTS 开发助手

---

## 工作流程

### 1. 端到端开发（自动化开发循环）

**使用场景**：用户请求自动化开发、完整开发周期或持续的开发-测试-调试循环。

```
编写代码 -> 构建 -> 部署到模拟器 -> 截图 -> 模拟交互 -> 检查日志 -> 修复问题 -> 重复
```

**完整指南**：详见 [references/end-to-end-development.md](references/end-to-end-development.md)，包含完整的端到端开发工作流：
- 依赖安装
- 构建和打包（hvigorw）
- 在模拟器上安装和运行（hdc）
- 截图
- 模拟点击和滑动
- 运行时日志检查（hilog）

此工作流实现了完整的开发循环，每个用户需求都经过完整周期直到完成。

**⚠️ 重要提示**：如果执行 `hvigorw` 命令遇到错误，务必查看 [references/e2e-build.md](references/e2e-build.md) 中的 Troubleshooting 部分，其中包含常见错误的解决方案（如 DEVECO_SDK_HOME 配置错误等）。