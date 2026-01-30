# 截图

从模拟器截取屏幕图像，用于观察界面布局和按钮位置。

## 基本用法

### 1. 在模拟器中截图

```bash
hdc shell snapshot_display -f /data/local/tmp/<随机文件名>.jpeg
```

示例：
```bash
hdc shell snapshot_display -f /data/local/tmp/snapshot_2026-01-25_21-38-31.jpeg
```

**建议**：使用时间戳作为文件名，避免文件名冲突。

### 2. 将截图传输到电脑

```bash
hdc file recv "/data/local/tmp/<截图文件名>" "<电脑上的文件夹的绝对路径>"
```

示例：
```bash
hdc file recv "/data/local/tmp/snapshot_2026-01-25_21-38-31.jpeg" "/Users/cxk/screenshots"
```

## 使用场景

截图主要用于：

1. **确认界面渲染** - 检查 UI 是否正确显示
2. **定位按钮位置** - 获取按钮的像素坐标，用于后续的模拟点击
3. **调试布局问题** - 观察组件的实际位置和大小
4. **记录测试结果** - 保存应用运行状态

## 注意事项

- 截图文件保存在模拟器的 `/data/local/tmp/` 目录
- 使用完毕后建议删除临时截图文件，避免占用空间
- 截图格式为 JPEG

## 参考文档

完整文档见：[HarmonyOS 开发工具 - hdc](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/hdc)
