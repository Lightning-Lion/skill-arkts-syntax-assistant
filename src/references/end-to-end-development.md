# 鸿蒙端到端开发指南

本指南提供完整的端到端开发流程，可以形成"编写代码、静态错误检查、运行到模拟器、模拟点击、运行时日志检查"的闭环。

**适用平台**: macOS（主要）、Windows

**适用场景**: 当用户要求全自动开发或完整的开发-测试-调试循环时使用本指南。

## 开发循环流程

用户每给出一个需求，按以下步骤循环执行：

1. **编写代码** - 实现功能
2. **编译打包** - 构建调试包
3. **安装到模拟器** - 部署应用
4. **启动应用** - 在模拟器中运行
5. **截图观察** - 查看界面和按钮位置
6. **模拟交互** - 点击/滑动操作
7. **查看日志** - 检查运行时日志
8. **根据反馈修改** - 分析问题并改进

**⚠️ 调试策略**：如果在模拟器测试时遇到写操作困难（比如缺少关键日志、无法定位问题），应果断回到步骤1（编写代码），在代码中增加合适的 debug 日志（使用自定义 emoji Tag），以便在后续步骤中获得更多反馈信息。不要在日志不足的情况下盲目调试。

循环以上步骤，直到完成用户的需求。

## 详细步骤文档

| 步骤 | 文档 |
|------|------|
| 安装依赖 | [e2e-dependencies.md](e2e-dependencies.md) |
| 编译打包 | [e2e-build.md](e2e-build.md) |
| 安装和运行 | [e2e-install-run.md](e2e-install-run.md) |
| 截图 | [e2e-screenshot.md](e2e-screenshot.md) |
| 模拟交互 | [e2e-interaction.md](e2e-interaction.md) |
| 运行时日志 | [e2e-logging.md](e2e-logging.md) |

## 快速参考

### 编写代码
不需要特殊说明，按照 ArkTS 语法编写即可。

### 工具路径参考

#### macOS
- ohpm: `/Applications/DevEco-Studio.app/Contents/tools/ohpm/bin/ohpm`
- hdc: `/Applications/DevEco-Studio.app/Contents/sdk/default/openharmony/toolchains`

#### Windows
- ohpm: `<DevEco Studio 安装目录>\ohpm\bin\ohpm`
- hdc: `<DevEco Studio 安装目录>\sdk\default\openharmony\toolchains\hdc.exe`

## 注意事项

1. **模拟器检查**: 首次使用前检查 `/var/root/Library/Huawei/Sdk` 确认模拟器已安装
2. **设备连接**: 使用 `hdc list targets` 确认模拟器已启动
3. **签名配置**: 真机调试需要配置签名，模拟器不需要
4. **日志标记**: 建议在代码中使用自定义 emoji Tag 便于日志筛选
