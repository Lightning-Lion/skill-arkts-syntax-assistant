# 安装依赖

在编译项目前，需要先安装项目依赖。

## macOS

```bash
/Applications/DevEco-Studio.app/Contents/tools/ohpm/bin/ohpm install --all --registry https://ohpm.openharmony.cn/ohpm/
```

## Windows

```bash
<DevEco Studio 安装目录>\ohpm\bin\ohpm install --all --registry https://ohpm.openharmony.cn/ohpm/
```

## 说明

- `--all`: 安装所有依赖包
- `--registry`: 指定 ohpm 仓库地址
- 该命令会读取项目的 `oh-package.json5` 文件并安装所有声明的依赖

## 常见问题

### 找不到 ohpm 命令

如果系统提示找不到 ohpm 命令，请检查 DevEco Studio 的安装路径：

- **macOS**: `/Applications/DevEco-Studio.app/Contents/tools/ohpm/bin/`
- **Windows**: `<DevEco Studio 安装目录>\ohpm\bin\`

可以将该路径添加到系统 PATH 环境变量中，或使用完整路径执行命令。
