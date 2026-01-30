# 安装和运行到模拟器

将编译好的 HAP 包安装到模拟器并启动应用。

## 前置检查

### 1. 检查模拟器是否已安装

检查目录 `/var/root/Library/Huawei/Sdk`，如果不存在或为空，说明未安装模拟器。

**未安装时的处理**：告诉用户需要在 DevEco Studio 中手动安装模拟器。参见下方"手动安装模拟器"部分。

### 2. 检查模拟器是否已启动

```bash
hdc list targets
```

如果没有输出设备列表，说明模拟器未启动。

**未启动时的处理**：告诉用户需要手动启动模拟器。参见下方"启动模拟器"部分。

#### hdc 命令位置

如果找不到 hdc 命令，检查以下位置：

- **macOS**: `/Applications/DevEco-Studio.app/Contents/sdk/default/openharmony/toolchains`
- **Windows**: `<DevEco Studio 安装目录>\sdk\default\openharmony\toolchains\hdc.exe`

## 安装和运行步骤

### 1. 停止并卸载旧版本

```bash
# 停止应用（替换为实际的包名）
hdc shell aa force-stop com.example.myapplication

# 卸载应用
hdc uninstall com.example.myapplication
```

### 2. 创建临时目录

生成一个 32 字符的随机字符串作为临时目录名（仅使用小写字母和数字）。

示例（实际使用时需要生成新的随机字符串）：
```bash
hdc shell mkdir data/local/tmp/3673588d101f4c3a96b1b64e1929eb96
```

### 3. 上传 HAP 文件

```bash
hdc file send "<HAP文件的绝对路径>" "data/local/tmp/<随机字符串>"
```

示例：
```bash
hdc file send "/Users/cxk/DevEcoStudioProjects/MyApplication/entry/build/default/outputs/default/entry-default-unsigned.hap" "data/local/tmp/3673588d101f4c3a96b1b64e1929eb96"
```

### 4. 安装应用

```bash
hdc shell bm install -p data/local/tmp/<随机字符串>
```

#### 签名错误处理

如果出现 `error: no signature file` 错误，说明项目未配置签名。

**注意**：模拟器不要求签名，此错误仅在真机调试时出现。

**解决方法**：

##### 中文界面
打开项目的 Project Structure，点开 Signing Configs，勾选 Automatically generate signature。如果显示 "Failed to auto generate signing, please sign in first."，点击 Sign In 完成登录后点击右下角的 OK。

##### 英文界面
打开项目的 Project Structure，点开 Signing Configs，勾选 Automatically generate signature。如果显示 "Failed to auto generate signing, please sign in first."，点击 Sign In 完成登录后点击右下角的 OK。

### 5. 清理临时文件

```bash
hdc shell rm -rf data/local/tmp/<随机字符串>
```

### 6. 启动应用

```bash
hdc shell aa start -a EntryAbility -b com.example.myapplication
```

**注意**：
- `-a EntryAbility`: 指定要启动的 Ability 名称
- `-b com.example.myapplication`: 指定应用包名

## 手动安装模拟器

### macOS

#### 中文界面
1. 打开 DevEco Studio，打开项目
2. 点击顶部菜单栏的"工具"，点开二级菜单的"设备管理器"
3. 点击右下角的"+新建模拟器"按钮
4. 在弹出窗口左侧的"类型"栏中选择"手机"
5. 在右侧设备列表中找到"版本（API）"最高的 Huawei_Phone
6. 点击该行右侧的下载按钮，开始下载
7. 下载完成后点击"完成"
8. 在"DevEco虚拟设备配置"窗口点击右下角的"下一步"
9. 在下一页中什么也不用改，点击右下角的"完成"
10. 看到"设备创建成功。"弹窗后，点击"确认"
11. 在"设备管理器"窗口的列表中可以看到设备，点击"操作"栏的启动按钮

#### 英文界面
1. 打开 DevEco Studio，打开项目
2. 点击顶部菜单栏的 Tools，点开二级菜单的 Device Manager
3. 点击右下角的"+ New Emulator"按钮
4. 在弹出窗口左侧的 Type 栏中选择 Phone
5. 在右侧设备列表中找到 Version（API）最高的 Huawei_Phone
6. 点击该行右侧的下载按钮，开始下载
7. 下载完成后点击"Finish"
8. 在"DevEco Virtual Device Configuration"窗口点击右下角的"Next"
9. 在下一页中什么也不用改，点击右下角的"Finish"
10. 看到"The device is successfully created."弹窗后，点击"OK"
11. 在"Device Manager"窗口的列表中可以看到设备，点击"Actions"栏的启动按钮

### Windows

#### 中文界面
1. 打开 DevEco Studio，打开项目
2. 点击左上角的菜单按钮，菜单列表中的"工具"点开，点开二级菜单的"设备管理器"
3. 点击右下角的"+新建模拟器"按钮
4. 在弹出窗口左侧的"类型"栏中选择"手机"
5. 在右侧设备列表中找到"版本（API）"最高的 Huawei_Phone
6. 点击该行右侧的下载按钮，开始下载
7. 下载完成后点击"完成"
8. 在"DevEco虚拟设备配置"窗口点击右下角的"下一步"
9. 在下一页中什么也不用改，点击右下角的"完成"
10. 看到"设备创建成功。"弹窗后，点击"确认"
11. 在"设备管理器"窗口的列表中可以看到设备，点击"操作"栏的启动按钮

#### 英文界面
1. 打开 DevEco Studio，打开项目
2. 点击左上角的菜单按钮，菜单列表中的"Tools"点开，点开二级菜单的"Device Manager"
3. 点击右下角的"+ New Emulator"按钮
4. 在弹出窗口左侧的 Type 栏中选择 Phone
5. 在右侧设备列表中找到 Version（API）最高的 Huawei_Phone
6. 点击该行右侧的下载按钮，开始下载
7. 下载完成后点击"Finish"
8. 在"DevEco Virtual Device Configuration"窗口点击右下角的"Next"
9. 在下一页中什么也不用改，点击右下角的"Finish"
10. 看到"The device is successfully created."弹窗后，点击"OK"
11. 在"Device Manager"窗口的列表中可以看到设备，点击"Actions"栏的启动按钮

## 启动模拟器

### macOS

#### 中文界面
1. 打开 DevEco Studio，打开项目
2. 点击顶部菜单栏的"工具"，点开二级菜单的"设备管理器"
3. 在"设备管理器"窗口的列表中可以看到设备，点击"操作"栏的启动按钮

#### 英文界面
1. 打开 DevEco Studio，打开项目
2. 点击顶部菜单栏的 Tools，点开二级菜单的 Device Manager
3. 在"Device Manager"窗口的列表中可以看到设备，点击"Actions"栏的启动按钮

### Windows

#### 中文界面
1. 打开 DevEco Studio，打开项目
2. 点击左上角的菜单按钮，菜单列表中的"工具"点开，点开二级菜单的"设备管理器"
3. 在"设备管理器"窗口的列表中可以看到设备，点击"操作"栏的启动按钮

#### 英文界面
1. 打开 DevEco Studio，打开项目
2. 点击左上角的菜单按钮，菜单列表中的"Tools"点开，点开二级菜单的"Device Manager"
3. 在"Device Manager"窗口的列表中可以看到设备，点击"Actions"栏的启动按钮

## 参考文档

- [HarmonyOS 开发工具 - hdc](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/hdc)
- [HarmonyOS 开发工具 - aa](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/aa-tool)
- [HarmonyOS 开发工具 - bm](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/bm-tool)
