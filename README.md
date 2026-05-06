# AppInfoScanner 用户手册

> 版本：v0.1.0  
> 适用平台：macOS (Apple Silicon)

---

## 1. 安装与启动

### 1.1 安装 DMG

>  *（双击 dmg → 拖入 Applications）*

![image](assets/image-20260429112344-gzj7u2g.png)

> 使用配置

配置jadx路径和adb路径，默认读取环境变量

![image](assets/image-20260429144915-ug8h6s8.png)

### 1.2 主工作台

> 实时扫描任务

拖入APK或者dex文件，点击扫描即可开始分析，代码分析可在java和smali中切换，默认分析为java源码

![image](assets/image-20260429111505-iwu2rmd.png)

> 任务管理

![image](assets/image-20260429112518-9jzg7iv.png)

> 扫描结果，命中结果高亮展示

![image](assets/image-20260429112539-yw7u2lw.png "敏感信息")

> 资产图谱

![image](assets/image-20260506131739-avjfm4y.png "资产图谱")

> 可通过激活来切换扫描的源

![image](assets/image-20260506131818-w8pvh91.png)

> 提取的URL列表

![image](assets/image-20260429112813-bvjc0lx.png "URL列表")

> 带壳APK扫描，判断56.al平台是否存在结果

![image](assets/image-20260506112651-tl2gt2t.png)

![image](assets/image-20260506114620-zlbr5t6.png)

---

## 2. 设备舰队

入口：左侧菜单 → **设备舰队**。

### 2.1 无设备状态

> *此功能需要先配置好adb路径（环境变量）*

![image](assets/image-20260429145611-usphu8s.png "设备舰队")

> 新增设备，点击+可以批量新增设备

![image](assets/image-20260429145754-8rxvcdo.png "连接adb设备")

### 2.2 已连接设备

> 在线设备包括所有尝试连接的设备（包含连接失败的设备），就绪设备为已经连接成功的设备，就绪设备会默认获取adb devices中的所有设备

![image](assets/image-20260506142719-y1b63pp.png)

> 实战可以针对adb未授权进行利用（下图为旧版本）
>
> ![image](assets/image-20260506142648-kum7954.png)

---

## 3. 屏幕镜像

### 3.1 未启动 / 启动

> 默认不启用屏幕镜像，可手动开启

![image](assets/image-20260429150045-qiy87xw.png "屏幕镜像（关闭）")

> 通过滑动鼠标可直接进行操控

![image](assets/image-20260429150146-w9v0jkn.png "屏幕镜像（开启）")

> 可开启独立窗口，操作延迟更低（需要安装scrcpy，配置环境变量）

![image](assets/image-20260429150310-y9dg8ck.png "独立窗口")

---

## 4. 文件管理

> 路径：右侧 Tab → **文件**。`/sdcard/` 默认入口。

![image](assets/image-20260429150604-4i7dj5y.png "文件管理")

### 4.1 下载

![image](assets/image-20260429150644-uqv0q6j.png "文件下载")

### 4.2 上传

![image](assets/image-20260429150734-oovr590.png "文件上传")

### 4.3 删除

![image](assets/image-20260429150759-ygh4nsl.png "文件删除")

---

## 5. 设备终端

> 交互式终端

![image](assets/image-20260429150849-isey4wm.png)

---

## 6. 应用管理

> 启动、停止、应用信息、清除数据、删除

![image](assets/image-20260429151002-kg8bg3g.png "应用列表")

---

## 7. 抓包

> mitm抓包，启动前可设置上游代理和自定义端口

![image](assets/image-20260429165829-b8a96zj.png "抓包")

---

## 8. 布局检查（暂时不可用）

---

## 9. 静态分析（MobSF）

> 参考MobSF静态分析进行了部分移植，点击开始分析后即可进行扫描

![image](assets/image-20260429170307-ha03a1a.png "静态分析")

> 分析记录

![image](assets/image-20260429170437-b26os9c.png "分析结果")

> 报告导出

![image](assets/image-20260429170722-a2764dz.png "报告导出")

‍

---

## 10. 逆向工作台

> 选择apk后创建会话，会话列表可以看到，可以看到可用工具，这部分功能和扫描任务中的功能类似，目前可执行的工具为jadx和mobsf，执行之后即可在下方产物浏览中查看结果，本质是吧前面两个模块的部分功能整合到这里

![image](assets/image-20260429172131-itub39s.png "逆向工作台")

> 产物浏览，执行jadx后可以看到反编译后的结果

![image](assets/image-20260429174929-ba5t01i.png)

---

## 13. Agent / MCP 集成

> 开启agent，点击右上角的机器人按钮

![image](assets/image-20260429175442-vmzrkw7.png)

> 模型配置，点击agent对话右上角的⚙️，可配置api，图中的配置是本地反代的codex，可自定义上下文长度，右上角可以看到当前会话的上下文和消耗的token

![image](assets/image-20260429175548-qj2j777.png)

> 对话

![image](assets/image-20260429175521-pfk0r2o.png)

> MCP服务器，可自己添加MCP服务器，平台能力也集成为appinfoscnner的mcp_server

![image](assets/image-20260429175953-xqfmnul.png)

![image](assets/image-20260429180007-4d9r0ta.png)

> 示例配置

```json
{
  "mcpServers": {
    "appinfoscanner": {
      "type": "stdio",
      "url": "",
      "command": "/xxxxxxxxxx/3.12.5/bin/python3",
      "args": [
        "/Users/xxxxx/AppInfoScanner-master/mcp_server.py"
      ],
      "env": {
        "APPINFOSCANNER_API": "http://127.0.0.1:5001",
        "NO_PROXY": "127.0.0.1,localhost",
        "no_proxy": "127.0.0.1,localhost",
        "ALL_PROXY": "",
        "all_proxy": "",
        "HTTP_PROXY": "",
        "http_proxy": "",
        "HTTPS_PROXY": "",
        "https_proxy": ""
      },
      "cwd": "",
      "enabled": true,
      "method_allowlist": null,
      "tool_type": "platform"
    },
    "jdax": {
      "type": "stdio",
      "url": "",
      "command": "uv",
      "args": [
        "--directory",
        "/Users/xxxxxxxx/jadx-mcp-server/",
        "run",
        "jadx_mcp_server.py"
      ],
      "env": {
        "NO_PROXY": "127.0.0.1,localhost",
        "no_proxy": "127.0.0.1,localhost",
        "ALL_PROXY": "",
        "all_proxy": "",
        "HTTP_PROXY": "",
        "http_proxy": "",
        "HTTPS_PROXY": "",
        "https_proxy": ""
      },
      "cwd": "",
      "enabled": true,
      "method_allowlist": null,
      "tool_type": "jadx"
    },
    "ida-pro-mcp": {
      "type": "stdio",
      "url": "",
      "command": "/xxxxxxxxxx/3.12.5/bin/python3",
      "args": [
        "/xxxxxxxxxxxxxxxx/ida_pro_mcp/server.py",
        "--ida-rpc",
        "http://127.0.0.1:13337"
      ],
      "env": {
        "ALL_PROXY": "",
        "HTTPS_PROXY": "",
        "HTTP_PROXY": "",
        "NO_PROXY": "127.0.0.1,localhost",
        "all_proxy": "",
        "http_proxy": "",
        "https_proxy": "",
        "no_proxy": "127.0.0.1,localhost"
      },
      "cwd": "",
      "enabled": false,
      "method_allowlist": null,
      "tool_type": "ida"
    },
    "frida-mcp": {
      "type": "stdio",
      "url": "",
      "command": "/xxxxxxxxx/3.12.5/bin/python3",
      "args": [
        "/Users/xxxxxxxxxxxxx/frida-mcp-main/frida_mcp.py"
      ],
      "env": {
        "ALL_PROXY": "",
        "HTTPS_PROXY": "",
        "HTTP_PROXY": "",
        "NO_PROXY": "127.0.0.1,localhost",
        "all_proxy": "",
        "http_proxy": "",
        "https_proxy": "",
        "no_proxy": "127.0.0.1,localhost"
      },
      "cwd": "",
      "enabled": false,
      "method_allowlist": null,
      "tool_type": "frida"
    }
  }
}
```

> firda脚本列表，可编辑，删改

![image](assets/image-20260429180148-i1fs975.png)

> 可调用agent生成frida脚本，脚本可以添加到frida 脚本列表保存

![image](assets/image-20260429173242-cd7l7wt.png)

> 保存到为bypass_ssl.js

![image](assets/image-20260429173624-jdna592.png)

---

## 12. Frida 脚本

> 点击agent界面右上角的⚡️按钮，可以看到当前加入的脚本列表

![image](assets/image-20260506095058-y9jc7ek.png "脚本列表")

> 脚本执行和输出

![image](assets/image-20260506095013-w6dbsbi.png "脚本执行")

![image](assets/image-20260506094951-v3fyqf4.png "脚本输出")

![image](assets/image-20260506100639-jaufrq9.png "可交互式输出")

---

## 14. 系统配置

> 配置首页

![image](assets/image-20260506131838-nmhqpk5.png "系统配置")

![image](assets/image-20260506131924-pl1tiv4.png "Android")

![image](assets/image-20260506131933-uuhefw3.png "加壳检测")

![image](assets/image-20260506131956-yuwsrls.png "云脱壳配置")
