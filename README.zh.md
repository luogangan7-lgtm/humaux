<div align="center">

<img src="assets/humaux-mark.svg" width="76" alt="Humaux" />

# Humaux

**为人而造。**

面向 AI 智能体的、以人为中心的辅助工具 —— 让 AI 自动化的完整链条
*围绕人来构建,而不是凌驾于人之上。*

[English](README.md) · 简体中文 · [Français](README.fr.md) · [Italiano](README.it.md)

[**humaux.com**](https://humaux.com) · [Humaux Memory](https://humaux.com/humauxmemory)

</div>

---

> ### ⚡ 一句话完成配置
> 对你的智能体说:**“读一下 https://github.com/luogangan7-lgtm/humaux,帮我配置 Humaux Memory。”**
> 它会照 **[SETUP.md](SETUP.md)** 自己配置到正确的文件里 ——
> 如果没有 `CLAUDE.md` / `AGENTS.md` / `.cursor/rules`,它会创建。
> 想手动配?见 [一行接入](#一行接入)。

## Humaux 是什么

智能体越来越能干,但它们缺的是**连续性** —— 每次会话结束,它们就忘了你是谁、
你做过什么决策、它们已经学到了什么。

Humaux 构建那一层"留得下来"的东西。不是更大的模型,也不是又一个智能体,而是
**以人为形状的记忆与工具** —— 让你所有的智能体接入同一层,把整条工作链围绕你来构建。

<div align="center">
<img src="assets/why.png" width="880" alt="没有共享记忆时,每次会话从零开始;有了 Humaux,智能体接着上次继续。" />
</div>

我们的路线图分三步:

| 阶段 | 产品 | 状态 |
|---|---|---|
| **1 · 记忆** | 所有智能体共享的一份结构化记忆 | **已上线** |
| 2 · 内容管道 | 把原始工作沉淀成可复用的结构化知识 | 进行中 |
| 3 · 自动化链 | 打通从意图到结果的闭环 | 规划中 |

---

## Humaux Memory

> 你的智能体共享的第二大脑。

一份持久、结构化的记忆,让每一个智能体 —— **Claude Code、Cursor、Codex、
Windsurf、Gemini CLI、Cline** 等等 —— 通过 [MCP](https://modelcontextprotocol.io) 接入。
存一次,处处可召回。它记住的是**决策,而不只是聊天记录** ——
结构化、经过佐证,并连同来源一起返回。

<div align="center">
<img src="assets/how-it-works.png" width="920" alt="Humaux Memory 工作原理:智能体经 MCP 接入一份共享记忆,含认知管道(抽取·连接·画像·技能)、知识图谱与代码图谱。" />
</div>

### 它能做什么

| | |
|---|---|
| **一份记忆,所有智能体** | 用 MCP 接入一次,你用的每个工具都共享同一个第二大脑。 |
| **认知分层** | 原始笔记经管道蒸馏 —— 原子 → 场景 → 画像 → 可复用技能 —— 而不是堆成一条流水日志。 |
| **知识图谱** | 记忆连成图;矛盾用双时间轴消解,最新的事实生效,历史完整保留。 |
| **代码图谱** | 把正在开发的代码传上来,查它的结构 —— 调用方、依赖、影响面 —— 代替重读整个文件,省 token。 |
| **自动画像** | Humaux 学习你是谁、你怎么工作,并注入到每个已连接的智能体 —— 你无需反复自我介绍。 |
| **公共知识池** | 自愿共享的知识,仅在被独立佐证后才对外提供。 |
| **自带模型** | 用你自己的 LLM 和向量模型。你的数据,加密存储,随时可导出。 |

> 全部工具及其**强制**使用约束:**[TOOLS.md](TOOLS.md)** · 自助安装指南:**[SETUP.md](SETUP.md)**。

### 一行接入

Claude Code:

```bash
claude mcp add --transport http humaux-memory https://humaux.com/memory/mcp \
  --header "Authorization: Bearer <你的令牌>"
```

其他任意 MCP 客户端(Cursor、Codex、Windsurf……):

```bash
npx -y humaux-memory-mcp --token <你的令牌>
```

在 **[humaux.com → 接入](https://humaux.com/humauxmemory)** 获取你的令牌。新工具在服务端
上线,你的智能体会自动获得 —— 无需重装。

<div align="center">
<img src="assets/connect.png" width="880" alt="Humaux 接入页:端点与令牌、14+ 客户端一键配置、以及你的智能体获得的工具。" />
<br/><sub>产品内的接入页 —— 一个端点,所有客户端,令牌已打码。</sub>
</div>

### 教你的智能体用起来

记忆用得最好的时候,是智能体主动去用它。把下面这段贴进你智能体的常驻规则
(`CLAUDE.md`、`AGENTS.md`、`.cursor/rules`……):

```text
会话开始、回答前,先在记忆里检索相关上下文。
学到决策、偏好、修复、项目进展,就立即存下来。
优先采信经过佐证的记忆;能从记忆召回的,别再问用户。
```

---

## 原则

- **围绕人。** 工具增强你,不替代你的判断,也不隐藏它做了什么。
- **记住决策,而非逐字记录。** 结构与来源,优先于原始日志。
- **默认诚实。** 经佐证的知识会被标注;单一来源的说法会谨慎对待。
- **你的数据属于你。** 自带模型;随时导出。

---

## 链接

- 🌐 官网 —— **[humaux.com](https://humaux.com)**
- 🧠 Humaux Memory —— **[humaux.com/humauxmemory](https://humaux.com/humauxmemory)**
- 📦 连接器 —— npm 上的 [`humaux-memory-mcp`](https://www.npmjs.com/package/humaux-memory-mcp)

<div align="center">
<sub>© Humaux · 为人而造。</sub>
</div>
