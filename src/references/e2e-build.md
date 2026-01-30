# 编译打包

编译项目生成调试包（HAP 文件）。

**⚠️ 重要提示**：如果执行 `hvigorw` 命令遇到错误，请务必查看本文档末尾的 **Troubleshooting** 部分，其中包含常见错误的解决方案。

## Phone 项目

```bash
hvigorw --mode module -p module=entry@default -p product=default -p requiredDeviceType=phone assembleHap --analyze=normal --parallel --incremental --daemon
```

## Wearable 项目

```bash
hvigorw --mode module -p module=entry@default -p product=default -p requiredDeviceType=wearable assembleHap --analyze=normal --parallel --incremental --daemon
```

## 参数说明

- `--mode module`: 模块编译模式
- `-p module=entry@default`: 指定编译 entry 模块
- `-p product=default`: 使用 default 产品配置
- `-p requiredDeviceType=phone/wearable`: 指定设备类型
- `assembleHap`: 编译生成 HAP 包
- `--analyze=normal`: 正常分析模式
- `--parallel`: 并行编译
- `--incremental`: 增量编译
- `--daemon`: 使用守护进程加速编译

## hvigorw 位置

如果项目中没有 hvigorw，可以使用 DevEco Studio 自带的 hvigorw：

### MacOS

```
/Applications/DevEco-Studio.app/Contents/tools/hvigor/bin/hvigorw
```

### Windows

```
<DevEco Studio 安装目录>\hvigor\bin\hvigorw
```

## 输出位置

编译成功后，HAP 文件通常位于：

```
<项目根目录>/entry/build/default/outputs/default/entry-default-unsigned.hap
```

## ⚠️ Troubleshooting（故障排除）

### Error: Invalid DEVECO_SDK_HOME

If you encounter the following error when running `hvigorw`:

```
Error: Exit code 255
> hvigor ERROR: 00303217 Configuration Error
Error Message: Invalid value of 'DEVECO_SDK_HOME' in the system environment path.
```

**Solution:** Set the required environment variables. **Note: Replace `cxk` with your actual username.**

```bash
export DEVECO_SDK_HOME=/Applications/DevEco-Studio.app/Contents/sdk
export JAVA_HOME=/Applications/DevEco-Studio.app/Contents/jbr/Contents/Home
export HOME=/Users/cxk
export SUDO_COMMAND=/Applications/DevEco-Studio.app/Contents/MacOS/devecostudio
export NODE_HOME=/Applications/DevEco-Studio.app/Contents/tools/node
```

## 参考文档

完整文档见：[HarmonyOS 命令行工具 - hvigor](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-hvigor-commandline)
