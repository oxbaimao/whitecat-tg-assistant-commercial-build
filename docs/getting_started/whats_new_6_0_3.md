# 🐱 白猫 TG 自动获客助手 · 旗舰商业版 v6.0.3

> 本版本是针对 v6.0.2 客户实战反馈的专项稳定与易用性升级：重点解决 **Bot 10.5 主动私信过住宅代理断连只拉不发图文、账号受限吞错刷出大量假坏号、创建 Bot 慢** 以及 **「实测私聊检测」排查 `@SpamBot` 误判号** 问题！

---

### 🌟 v6.0.3 核心修复与新增能力

#### 🔧 1. Bot 10.5 主动私信稳定性与报错透明大幅升级
- **过住宅 SOCKS5 代理不再只拉人、不发图文按钮**：
  - 底层 Bot API 自动将 `socks5://` 转为远端 DNS 解析 `socks5h://`；
  - 发送大图 / 文本 / 三色按钮时新增「**主代理双次重试 → 全局代理回退 → 直连兜底**」，不再因 `SSLEOFError` 直接中断批次，确保「拉进人 + 发图文卡片 + 带三色按钮」整套动作稳稳送达。
- **账号限制立即止损，不再误算“坏号”**：
  - 当协议号遇到 `PeerFloodError` / `FloodWaitError` / 冻结等账号侧限制时，**第 1 批立即停用该号**，把未发目标自动退回队列交由其他健康号接管（不再连续空烧 6 批 60 人或污染断点记录）。
- **报错全透明 + 6 路并发建 Bot**：
  - 底部「运行日志」实时打印每个账号的具体异常原因；「最近动态」关闭换行截断（不再只显示 `⚠ 无效/跳过 ...`），悬停即可看全文；所有异常日志中的 Bot Token 彻底打码隐藏；
  - 「一键每号创建专属 Bot」升级为 **6 路并发**，20 个号建 Bot 耗时成倍缩短，并自动随账号勾选刷新右侧明细表（同时优化了窄屏表头显示）。

#### 🧪 2. 账号中心新增「实测私聊检测」（破解 `@SpamBot` 误报难题）
- 部分号段会被 `@SpamBot` 回复 `"harsh response"` 并显示为「双向受限」，但实际仍能正常向陌生人发私信。
- 现在在「账号中心」工具栏直接点 **「🧪 实测私聊」**：填入你自己的测试接收号 `@username`，软件会真实发一条测试私信并 **回读聊天记录核验**：
  - **实测可送达**：可选自动将该账号的原「双向受限」状态恢复为「在线」，避免被自动过滤拦截；
  - **真受限（`PeerFloodError`） / 冻结**：如实标记受限；遇对方隐私拒绝则如实报「未核实」，绝不误伤。

---

### 📥 官方安装包下载与 SHA-256 校验

| 系统平台 | 类型 | 下载文件 | SHA-256 校验码 |
| :--- | :--- | :--- | :--- |
| **Windows x64** | 🌟 **安装版（自带更新）** | [WhiteCat-TG-Assistant-6.0.3-Setup.exe](https://license.web3baimao.com/api/v1/update/files/WhiteCat-TG-Assistant-6.0.3-Setup.exe) | `cfa33b6dfe6c60346cccc91d1677ff69f805efa5271edca773127360c7517d83` |
| **Windows x64** | **绿色便携版** | [WhiteCat-TG-Assistant-6.0.3-Windows-x64-Portable.zip](https://license.web3baimao.com/api/v1/update/files/WhiteCat-TG-Assistant-6.0.3-Windows-x64-Portable.zip) | `89a046ed6fef8992e3f2c9dadb8701bd7bb09bcb22be232640fc45339cf0a25c` |

> GitHub Release 同步发布：[v6.0.3](https://github.com/oxbaimao/whitecat-tg-assistant-commercial-build/releases/tag/v6.0.3)

---

### 💡 客户使用提示
- 如果接收方截图显示「**不支持的消息 — 请更新 Telegram 以查看此消息**」，代表接收方自己的 Telegram 客户端版本较老、未升级到 Bot API 10.5 协议层；建议先用最新版 Telegram 手机端/桌面端测试预览效果；
- 安装包未配置代码签名证书，Windows 首次运行如见 SmartScreen 提示请点「更多信息 → 仍要运行」。
