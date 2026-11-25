# PFBus 通信协议

[![规范版本: v1.5](https://img.shields.io/badge/规范-v1.5-blue.svg)](spec/v1.5/PFBus-Protocol-zh.txt)
[![开源许可证: Apache-2.0](https://img.shields.io/badge/License-Apache%202.0-green.svg)](LICENSE)
[![官方网站](https://img.shields.io/badge/官方入口-pfbus.net-orange.svg)](https://pfbus.net/zh/)

[English Readme](README.md) | [官方网站 (pfbus.net)](https://pfbus.net/zh/) | [v1.5 规范全文](spec/v1.5/PFBus-Protocol-zh.txt)

---

**PFBus (PocketFleet Bus)** 是一个开放、轻量、基于纯文本信封的人类与 AI、以及多 AI 之间的协同通信协议。

PFBus 定义了标准化的纯文本信封格式，用于在多个异构 AI 智能体之间路由消息、交接任务，以及主持结构化的多智能体研讨会议。

PFBus 协议独立于任何单一模型厂商或商业云服务。消息投递、会话调度与席位权限均由兼容的具体实现程序（如 My AI Buddies Bridge）在本地落实。

> **“PFBus 是通信协议，My AI Buddies 是基于该协议构建的官方软件产品。”**

---

## 🚀 15 秒极简语法

PFBus 信封必须顶格写在输出的**第一行**，正文从次行开始：

```text
[PFBus][mailto:@节点A];[waitReply]
请审查这段代码提交，并指出潜在的系统架构与并发风险。
```

### 标准格式
```text
[PFBus][mailto:%s];[cc:%s];[waitReply|noReply]
```
- **`mailto`**：唯一主收件人。AI 节点写 `@节点名称`；人类写其设定的人类称呼。
- **`cc`**：抄送对象，可选（仅在会议模式生效，多个节点用逗号分隔）。无抄送时整段连同分号省略。
- **`waitReply`**：需要对方回复以推进下一步任务。
- **`noReply`**：纯通知、广播或终局交差结单，防止产生死循环回声。

### 会议指令（仅在人类发起 /meet 会议时有效）
- `[PFBus][signup:%s]`：点名期报到指令，`%s` 为参会节点昵称。
- `[PFBus]/rules`：主持 AI 专属，次行紧跟任务分派与验收标准 JSON。
- `[PFBus]/meetover`：人类或主持 AI 发送以关闭会议，次行输出交付物路径与节点量化评分。

---

## 🛠️ 官方首发实现产品

### **[My AI Buddies（我的 AI 搭子们）](https://pfbus.net/zh/)**
My AI Buddies 是由 PFBus 协议制定团队打造的首个自有桌面实现产品。它通过本地 Windows 桥接程序与 Telegram，将主流网页端 AI（ChatGPT、Claude、Gemini、DeepSeek、Qwen、Grok、豆包）以及本地代码 AI 与人类工程师无缝编组。

- **免费配置**：开箱即提供 2 个 AI 席位免费使用。
- **保护隐私**：基于本地无障碍 API（UIA）与浏览器插件实现会话投递，零 API Key 需求，零云端中转截留。

---

## 🛡️ 安全承诺与非目标

PFBus 是一套严格的**纯文本应用层路由规范**：
- **不赋予系统执行权限**：PFBus 规范不包含任何操作系统提权、Shell 终端执行或沙箱逃逸要求。
- **零 SSRF 风险**：规范明确禁止要求 AI 模型调用 `curl`、扫描本地端口或请求 `127.0.0.1`。
- **纯文本中立隔离**：`[PFBus]` 仅作为信封标记由宿主桥接器解析，正文内容完全保持不透明原貌。

---

## 📂 仓库目录导引

- [`spec/`](spec/)：按版本归档的官方不可变规范文本（包含 `v1.0` 至 `v1.5` 全历史）。
- [`docs/`](docs/)：架构设计、会议状态机与已知实现清单。
- [`examples/`](examples/)：点对点通信与会议模式真实范例。
- [`test-vectors/`](test-vectors/)：解析器一致性测试用例集。
- [`ROADMAP.md`](ROADMAP.md)：工程路线图、多语言 SDK 发版规划与生态待办事项。

---

## 🗺️ 路线图与待办事项 (Roadmap)

详见 [`ROADMAP.md`](ROADMAP.md)：
- **阶段一（核心杠杆）**：多语言参考解析器与 SDK（`pfbus-python`、`@pfbus/core`、`pfbus-go`）。
- **阶段二（质量防线）**：一致性测试套件扩展与 GitHub Actions 跨语言自动化回归测试。
- **阶段三（生态扩展）**：PFBus CLI 校验工具及主流 Agent 框架（LangChain / MCP）桥接适配器。

---

## ⚖️ 治理与许可证

- **协议规范许可**：采用 [Apache License, Version 2.0](LICENSE) 开源发布。
- **治理规则**：任何人均可自由实现、使用或派生衍生协议。官方版本发布与品牌规范依据 [GOVERNANCE.md](GOVERNANCE.md) 执行。
