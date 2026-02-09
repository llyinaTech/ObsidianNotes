
### 1. 下载安装包

前往 [nvm 中文官网](https://nvm.uihtm.com/doc/download-nvm.html) 下载最新版本的安装包（推荐选择 `nvm-setup.exe`）。

### 2. 核心避坑：路径规划（极其重要）

在安装过程中，系统会先后要求你选择两个路径。**请务必确保这两个文件夹处于平级关系，而不是嵌套关系。**

#### ❌ 错误示范（会导致权限冲突或死循环）

Plaintext

```
D:\development\nvm         <-- nvm 安装在这里
D:\development\nvm\nodejs  <-- Node.js 映射路径在 nvm 内部（错误！）
```

#### ✅ 正确方案（平级目录）

Plaintext

```
D:\development\nvm         <-- nvm 程序根目录
D:\development\nodejs      <-- Node.js 快捷方式映射目录
```

---

### 3. 配置原因及原理

- **nvm 目录**：存放 nvm 运行程序以及你下载的所有不同版本的 Node.js 源码包。
    
- **nodejs 目录**：实际上是一个**符号链接（Symbolic Link）**。当你执行 `nvm use 18.0.0` 时，nvm 会把这个文件夹“指向”对应的版本。如果它在 nvm 内部，会导致路径解析逻辑混乱。
    

---

### 4. 验证安装是否成功

安装完成后，请打开 **PowerShell** 或 **CMD**（建议以管理员身份运行），输入以下命令验证：

1. **检查版本**：`nvm -v`
    
2. **设置国内镜像**（下载更快）：
    
    Bash
    
    ```
    nvm node_mirror https://npmmirror.com/mirrors/node/
    nvm npm_mirror https://npmmirror.com/mirrors/npm/
    ```
    
3. **安装并使用 Node**：
    
    Bash
    
    ```
    nvm install 20.10.0
    nvm use 20.10.0
    node -v
    ```
    

---

**💡 小贴士：** 如果安装前电脑里已经装过独立的 Node.js，请先将其**彻底卸载**，否则会发生路径冲突，导致 nvm 无法切换版本。