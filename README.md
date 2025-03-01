# ObserverRespawnTimer - SCP:SL 观察者重生倒计时插件

![GitHub License](https://img.shields.io/badge/EXILED-5.0.0+-blue)  
![SCP:SL Version](https://img.shields.io/badge/SCP:SL-≥12.0.0-red)  

---

## 🕹️ **插件功能**  
为《SCP: Secret Laboratory》玩家提供死亡后的倒计时与重生管理工具。

### 核心特性  
- **死亡倒计时显示**  
  - 在屏幕指定位置（如底部/顶部）显示精确到秒的重生时间。  
  - 支持自定义文字颜色（HEX 格式，如 `#FF0000`）和计时格式（`mm:ss` 或纯秒数）。  

- **广播通知**  
  - 可选向全体玩家或阵营频道发送倒计时提醒（例如：`[系统] 重生剩余: 00:15`）。  

- **管理员指令**  
  - 权限指令（如 `!respawn skip`）允许管理员跳过等待或重置倒计时。  

- **多语言适配**  
  - 提供中英双语配置文件，支持扩展其他语言（如日文、韩文）。  

---

## 📥 **安装指南**

### 前置条件  
- 服务器已安装 [**EXILED 框架**](https://github.com/Exiled-Team/EXILED)（版本 ≥ 5.0.0）。

### 部署步骤  
1. **下载插件文件**  
   - 从 [Releases 页面](https://github.com/yourrepo/ObserverRespawnTimer/releases) 下载 `ObserverRespawnTimer.dll`。  

2. **安装依赖（可选）**  
   - 若插件需要额外库（如 `TextPlugin`），需一并放入 `Plugins/dependencies/` 目录。  

3. **配置插件**  
   - 将 DLL 文件复制到服务器路径：  
     ```bash
     /SCPSL/EXILED/Plugins/ObserverRespawnTimer.dll
     ```  
   - 首次启动后，编辑生成的配置文件：  
     ```yaml
     # /EXILED/Configs/observer_respawn_config.yml  
     is_enabled: true  
     countdown_position: Bottom  # 可选 Top/Custom  
     custom_x: 50               # 仅当 position=Custom 时生效  
     custom_y: 90  
     text_color: "#FFFFFF"  
     ```  

4. **权限设置**  
   - 在 `configs_permissions.txt` 中添加指令权限组：  
     ```text
     resetscptimer: owner,admin  
     skiprespawn: moderator  
     ```  

5. **重启服务器**  
   - 使用 `mpstart` 或控制面板重启服务以激活插件。  

---

## 🔧 **配置与使用**

### 指令列表  
| 指令                | 权限节点          | 功能描述               |  
|---------------------|-------------------|-----------------------|  
| `!respawn status`   | 无                | 查看当前倒计时状态     |  
| `!respawn skip`     | `skiprespawn`     | 管理员立即重生自己     |  
| `!respawn reset`    | `resetscptimer`   | 重置所有玩家的倒计时   |  

### 多语言切换  
1. 编辑 `/EXILED/Translations/observer_respawn.zh-CN.yml`：  
   ```yaml  
   CountdownText: "剩余时间: {time}"  
   BroadcastMsg: "玩家 {player} 将在 {time} 后重生！"  
