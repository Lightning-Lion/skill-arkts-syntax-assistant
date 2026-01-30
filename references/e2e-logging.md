# 运行时日志检查

使用 hilog 工具查看应用的运行时日志，用于调试和问题诊断。

## 基本用法

### 1. 清理旧日志

在运行应用前，建议先清理之前的日志，避免干扰：

```bash
hdc shell hilog -r
```

### 2. 筛选日志

使用正则表达式筛选特定标签的日志：

```bash
hdc shell hilog --regex <标签> --exit
```

参数说明：
- `--regex <标签>`: 使用正则表达式匹配日志标签
- `--exit`: 输出当前缓冲区的日志后退出（不持续监听）

### 示例

筛选包含自定义 emoji 标签 🔘 的日志：

```bash
hdc shell hilog --regex 🔘 --exit
```

## 推荐实践

### 使用自定义标签

在代码中使用独特的标签（如 emoji）便于日志筛选：

```typescript
import hilog from '@ohos.hilog';

const TAG = '🔘';  // 使用 emoji 作为标签

hilog.info(0x0000, TAG, 'Application started');
hilog.debug(0x0000, TAG, 'Button clicked: %{public}s', buttonName);
hilog.error(0x0000, TAG, 'Error occurred: %{public}s', errorMessage);
```

### 日志级别

hilog 支持多个日志级别：
- `debug`: 调试信息
- `info`: 一般信息
- `warn`: 警告信息
- `error`: 错误信息
- `fatal`: 致命错误

## 常用命令

### 持续监听日志

如果需要实时查看日志（不使用 --exit）：

```bash
hdc shell hilog --regex <标签>
```

按 Ctrl+C 停止监听。

### 查看所有日志

```bash
hdc shell hilog
```

### 清空日志缓冲区

```bash
hdc shell hilog -r
```

## 调试流程

1. **清理日志** - 运行 `hdc shell hilog -r` 清空旧日志
2. **运行应用** - 启动应用并执行操作
3. **查看日志** - 使用 `hilog --regex` 筛选相关日志
4. **分析问题** - 根据日志输出定位问题
5. **修改代码** - 修复问题后重新编译和部署
6. **重复验证** - 重复以上步骤直到问题解决

**⚠️ 重要提示**：如果在调试过程中发现日志信息不足以定位问题（例如缺少关键步骤的日志、无法判断代码执行路径），应立即回到编写代码步骤，在代码的关键位置添加更多 debug 日志。使用自定义 emoji Tag 可以方便后续筛选。充足的日志信息是高效调试的基础，不要在日志不足的情况下浪费时间猜测问题。

## 参考文档

完整文档见：[HarmonyOS 开发工具 - hilog](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/hilog)
