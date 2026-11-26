# Agentic Research：AI 辅助科研入门工具包

**English: see [README.md](README.md)**

这是一套开箱即用的入门工具包，帮助你借助 AI 助手完成科研：**从研究问题一直到投稿**，同时始终掌控你的文献、数据和结果。
它同时支持 **Claude Code**（Anthropic 公司）和 **Codex**（OpenAI 公司）：用其中一个或两个都用都可以。

你**不需要会编程**：只需安装几个应用，再粘贴三条简短的命令，下面有一步一步的说明。
适用于任何学科的学生和研究者。
文中所有信息均于 **2026 年 11 月 26 日**在各工具的官方页面核实。

**第一次使用？直接看 [一步一步安装所有工具](#一步一步安装所有工具)。**

---

## 一分钟了解思路

每篇论文放在电脑上的**一个文件夹**里。AI 助手（Claude Code 或 Codex）就在这个文件夹里工作：

- 它遵守你写好的**规则文件**（`AGENTS.md`），只需写一次；
- 它通过**插件**（称为 MCP 服务器）检索 22 个真实的学术数据库，并读取你的 Zotero 文献库；
- 它按照**技能**（skills，即步骤清单）完成文献综述、创新性检查、写作和引用核查；
- **Git** 保存每一个版本，任何修改都可以撤销。

让研究经得起审稿的四条规则：

1. **每一条引用都要打开原文核实**，绝不凭记忆引用。
2. **先冻结研究方案**（假设与分析计划），再看结果。
3. **用计划文件和进度文件**记录工作，这样你、合作者或任何 AI 都能接着做。
4. **文件里不放任何密钥**：API 密钥只保存在环境变量中。

## 用 Claude Code 还是 Codex？

| | Claude Code | Codex |
|---|---|---|
| 最简单的入口 | Claude 桌面应用 → **Code** 标签页 | ChatGPT 桌面应用（Codex） |
| 需要的套餐 | Claude 付费套餐（Pro 或以上） | 包含在 ChatGPT 各套餐中，包括 Free 和 Go |
| 规则文件 | `CLAUDE.md`（它会加载 `AGENTS.md`） | `AGENTS.md` |
| 插件设置（模板中已准备好） | `.mcp.json` | `.codex/config.toml` |
| 技能文件夹（模板中已准备好） | `.claude/skills/` | `.agents/skills/` |
| 调用技能 | `/技能名` | `$技能名` |

两者在本仓库中都已配置好。你可以随时切换，也可以让一个助手检查另一个的工作。

## 一步一步安装所有工具

**每台电脑只需做一次**，大约 30–45 分钟。不需要任何编程知识：你只需要点击安装程序，再粘贴**三条简短的命令**。

### 要安装什么，为什么

| 工具 | 用途 | 是否需要 |
|---|---|---|
| **Claude 桌面应用** 和/或 **ChatGPT 桌面应用** | 你的 AI 助手（Claude Code 在 Claude 应用里；Codex 在 ChatGPT 应用里） | 需要，至少一个 |
| **Zotero 10** + **Zotero Connector** | 文献库，以及在浏览器里一键保存论文的按钮 | 需要 |
| **Better BibTeX**（Zotero 插件） | 为每篇论文生成稳定的引用键 | 需要 |
| **uv** | 运行插件的小工具；需要时会自动下载 Python | 需要 |
| **Zotero 插件**（zotero-mcp） | 让助手读取你的 Zotero 文献库 | 需要 |
| **GitHub 账号** + **GitHub Desktop** | 保存工作的每一个版本，用按钮代替命令 | 推荐 |
| **茉莉花 Jasminum**（Zotero 插件） | 保存知网、万方、维普的中文论文 | 仅中文文献需要 |

**不需要安装 Python。** 插件需要时，uv 会自动下载。
**不需要 Node.js**，除非你以后想用 Codex 的命令行版本。
**论文检索插件不需要安装：** 助手第一次使用时，uv 会自动获取它。

### 开始之前：如何粘贴命令

只有三条命令需要用到这个方法。

- **Windows：** 按 **Windows 键**，输入 **PowerShell**，点击 **Windows PowerShell**，会出现一个文字窗口。
  从本页复制命令，在窗口里**点击鼠标右键**（即粘贴），然后按 **回车键**。
- **Mac：** 按 **Cmd + 空格**，输入 **终端**（或 **Terminal**），按回车。从本页复制命令，在窗口里按 **Cmd + V**，然后按回车。
- 每装完一样东西，**关闭窗口，再打开一个新窗口**，然后再做下一步。新安装的程序只有在新窗口里才能找到。

---

### Windows

**第 1 步 — AI 助手应用**（Windows 10 或更高版本）

- **Claude：** 打开 https://claude.com/download ，下载 Windows 版本，安装并登录。Claude Code 就是 **Code** 标签页，需要 Claude 付费套餐（Pro 或以上）。
- **ChatGPT（用于 Codex）：** 在 Microsoft Store 中安装 **ChatGPT**（或见 https://learn.chatgpt.com/docs/app ），然后登录。Codex 包含在 ChatGPT 各套餐中，包括免费版。

**第 2 步 — Zotero 10 和 Zotero Connector**

1. 打开 https://www.zotero.org/download/ ，下载 **Zotero for Windows** 并安装。
2. 在同一页面，点击按钮为你的浏览器（Chrome、Edge 或 Firefox）安装 **Zotero Connector**。
3. 打开 Zotero → **编辑 → 设置 → 高级** → 勾选 **“允许此计算机上的其他应用程序与 Zotero 通信”**
   （英文界面：Edit → Settings → Advanced → “Allow other applications on this computer to communicate with Zotero”）。

**第 3 步 — Better BibTeX**

1. 打开 https://github.com/retorquere/zotero-better-bibtex/releases/latest ，在 **Assets** 下载以 **.xpi** 结尾的文件。
   （用 Firefox 的话：右键点击文件 → **链接另存为…**，否则 Firefox 会尝试自己安装它。）
2. 在 Zotero 中：**工具 → 插件**（Tools → Plugins）→ 点击右上角的**齿轮**图标 → **从文件安装插件…**（Install Plugin From File…）→ 选择 .xpi 文件 → **安装**（Install）。
3. *中文文献：* 用同样的方法安装茉莉花的 .xpi 文件：https://github.com/l0o0/jasminum/releases 。中文说明：https://zotero-chinese.com

**第 4 步 — uv**（第 1 条命令，共 3 条）

打开 **PowerShell**，粘贴下面这一整行，然后按回车：

```
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

关闭 PowerShell，打开一个新的，输入 `uv --version` 并按回车，应该会显示一个版本号。

**第 5 步 — Zotero 插件**（第 2、3 条命令）

在 PowerShell 中逐行粘贴下面两行，每行后按回车：

```
uv tool install zotero-mcp-server
uv tool update-shell
```

关闭 PowerShell，打开一个新的，输入 `uv tool list` 并按回车：列表中应该有 **zotero-mcp-server**。

**第 6 步 — GitHub**（推荐）

1. 在 https://github.com/signup 注册免费账号。
2. 从 https://github.com/apps/desktop 安装 **GitHub Desktop**，并用这个账号登录。

**第 7 步 — 重启 AI 应用**

完全退出 Claude 或 ChatGPT 应用，再重新打开，这样它才能找到 uv 和 Zotero 插件。

---

### Mac

**第 1 步 — AI 助手应用**

- **Claude：** 打开 https://claude.com/download ，下载 Mac 版本（需要 macOS 13 Ventura 或更高版本），拖到“应用程序”文件夹，打开并登录。Claude Code 就是 **Code** 标签页（需要 Claude 付费套餐，Pro 或以上）。
- **ChatGPT（用于 Codex）：** 从 https://learn.chatgpt.com/docs/app 下载 Mac 应用（下载的是 Apple 芯片 Mac 的版本），然后登录。Codex 包含在 ChatGPT 各套餐中，包括免费版。

**第 2 步 — Zotero 10 和 Zotero Connector**

1. 打开 https://www.zotero.org/download/ ，下载 **Zotero for Mac**，打开后把 Zotero 拖到“应用程序”。
2. 在同一页面为你的浏览器安装 **Zotero Connector**（Safari 的已经包含在 Zotero 里）。
3. 打开 Zotero → **Zotero → 设置 → 高级**（Zotero → Settings → Advanced）→ 勾选 **“允许此计算机上的其他应用程序与 Zotero 通信”**
   （“Allow other applications on this computer to communicate with Zotero”）。

**第 3 步 — Better BibTeX**

与 Windows 第 3 步相同：从 https://github.com/retorquere/zotero-better-bibtex/releases/latest 下载 **.xpi** 文件，
然后在 Zotero 中 **工具 → 插件** → **齿轮** → **从文件安装插件…**。中文文献：同样安装茉莉花。

**第 4 步 — uv**（第 1 条命令，共 3 条）

打开 **终端**，粘贴下面这一行，然后按回车：

```
curl -LsSf https://astral.sh/uv/install.sh | sh
```

关闭终端，打开一个新的，输入 `uv --version` 并按回车，应该会显示一个版本号。

**第 5 步 — Zotero 插件**（第 2、3 条命令）

```
uv tool install zotero-mcp-server
uv tool update-shell
```

关闭终端，打开一个新的，输入 `uv tool list`：列表中应该有 **zotero-mcp-server**。

**第 6 步 — GitHub**（推荐）

在 https://github.com/signup 注册免费账号，然后从 https://github.com/apps/desktop 安装 **GitHub Desktop**（需要 macOS 12 或更高版本）并登录。
如果 Mac 提示安装 **“命令行开发者工具”**，点击 **安装** 即可：那是苹果提供的 Git。

**第 7 步 — 重启 AI 应用**

完全退出 Claude 或 ChatGPT 应用（Cmd + Q），再重新打开。

---

### 遇到问题怎么办

| 你看到的情况 | 怎么做 |
|---|---|
| 提示 `uv` 或 `zotero-mcp` “无法识别” / “command not found” | 关闭窗口，打开一个新窗口。还不行？重启电脑。 |
| Windows 提示禁止运行脚本 | 复制第 4 步中 uv 的**整行**命令，包括 `powershell -ExecutionPolicy ByPass`。 |
| 助手看不到 Zotero | Zotero 是否已打开？第 2 步的“允许其他应用程序……”是否已勾选？重启 AI 应用。 |
| 其他问题 | 复制错误信息，问你的助手：*“我在安装时遇到了这个错误，该怎么办？”* |

各步骤的官方页面：uv https://docs.astral.sh/uv/getting-started/installation/ ·
Zotero https://www.zotero.org/download/ · Better BibTeX https://retorque.re/zotero-better-bibtex/installation/ ·
Zotero 插件 https://github.com/54yyyu/zotero-mcp · GitHub Desktop https://docs.github.com/en/desktop

## 开始使用（每篇新论文）

1. **获取你自己的副本：** 在本 GitHub 页面点击 **Use this template** → **Create a new repository**（设为**私有**），
   然后在 GitHub Desktop 中用 **Clone repository** 把它下载到电脑上。
   没有 GitHub？点击 **Code → Download ZIP** 并解压。用论文名称命名，例如 `my-paper`。
2. **在助手中打开文件夹。** Claude：打开 **Code** 标签页并选择该文件夹，提示时批准项目的插件。
   Codex：在 ChatGPT 应用中打开该文件夹；如果询问是否信任该文件夹，请选择信任（插件只在受信任的文件夹中生效）。
3. **检查插件：** 输入 `/mcp`，应该能看到 **paper-search** 和 **zotero**。
4. **填写 `AGENTS.md`**，最简单的方法是让助手帮你：*“和我一起填写 AGENTS.md，每次只问我一个问题。”*
5. **可选：申请免费的 API 密钥**，让论文检索更快（见下文）。
6. **布置第一个任务**，例如（中英文都可以）：
   *“请阅读 AGENTS.md 和研究计划，然后用 literature-review 技能为 WP1.1 制定检索方案，把方案写进检索记录，然后停下来等我确认。”*
7. **保存版本：** 在 GitHub Desktop 中写一句简短说明，点击 **Commit to main**，然后点击 **Push origin**。

## API 密钥在哪里申请

API 密钥就像一张免费的“借书证”：有了它，论文检索插件可以向数据库请求更多、更快的结果。
**不申请任何密钥也可以开始**，只是速度慢一些，而且在你提供邮箱之前不会使用 Unpaywall。完整指南：`setup-guides/08-api-keys.md`。

| 数据库 | 是否需要 | 在哪里申请 | 费用 / 谁可以申请 | 环境变量名称 |
|---|---|---|---|---|
| Unpaywall（免费全文） | 需要，用于获取免费全文 | 无需注册，只要提供一个你选定的邮箱地址 | 免费 | `PAPER_SEARCH_MCP_UNPAYWALL_EMAIL` |
| Semantic Scholar | 推荐 | https://www.semanticscholar.org/product/api 填写申请表，密钥通过邮件发送 | 免费 | `PAPER_SEARCH_MCP_SEMANTIC_SCHOLAR_API_KEY` |
| CORE（开放获取论文） | 推荐 | https://core.ac.uk/services/api | 免费 | `PAPER_SEARCH_MCP_CORE_API_KEY` |
| OpenAlex | 可选（每天的额度增加 10 倍） | 在 https://openalex.org/signup 注册，然后在 Settings → API key 中复制 | 免费 | `PAPER_SEARCH_MCP_OPENALEX_API_KEY` |
| Web of Science（Starter API） | 可选 | https://developer.clarivate.com/apis/wos-starter | 任何人可免费试用（每天 50 次）；学校订阅后额度更多 | `PAPER_SEARCH_MCP_WOS_API_KEY` |
| Scopus（Elsevier） | 可选 | https://dev.elsevier.com/apikey/manage | 密钥免费，但必须通过**学校的订阅**才能获取数据，通常要在校园网内使用 | `PAPER_SEARCH_MCP_SCOPUS_API_KEY` |
| IEEE Xplore | 可选 | https://developer.ieee.org | 仅限 IEEE 订阅用户，非商业研究 | `PAPER_SEARCH_MCP_IEEE_API_KEY` |

**对大多数同学**：设置 Unpaywall 邮箱，再申请 Semantic Scholar、CORE 和 OpenAlex 的密钥即可。如果学校图书馆有 Scopus 或 Web of Science，再加上它们。

**Google Scholar** 没有官方 API，可能会拦截自动检索（出现验证码）；这时其他数据库仍然正常工作。

**中文文献**（知网、万方、维普）不通过这个插件检索：请在 Zotero 中安装茉莉花插件和中文转换器，把文献保存到 Zotero，
助手就能通过 Zotero 插件读取它们。中文指南：https://zotero-chinese.com/user-guide/faqs/update-translators.html

### 如何保存密钥（每台电脑只需一次）

绝不要把密钥粘贴到项目文件、聊天、幻灯片或邮件中，而是保存为**环境变量**。Claude Code 和 Codex 都会从那里读取。

**Windows（PowerShell）**：每个密钥一行，然后关闭并重新打开终端和应用：

```
setx PAPER_SEARCH_MCP_UNPAYWALL_EMAIL "your-chosen-email@example.org"
setx PAPER_SEARCH_MCP_SEMANTIC_SCHOLAR_API_KEY "在这里粘贴你的密钥"
setx PAPER_SEARCH_MCP_CORE_API_KEY "在这里粘贴你的密钥"
setx PAPER_SEARCH_MCP_OPENALEX_API_KEY "在这里粘贴你的密钥"
```

**Mac**：打开“终端”，输入 `touch ~/.zshrc && open -e ~/.zshrc`，在文件末尾加上下面几行，保存后打开一个新的终端窗口：

```
export PAPER_SEARCH_MCP_UNPAYWALL_EMAIL="your-chosen-email@example.org"
export PAPER_SEARCH_MCP_SEMANTIC_SCHOLAR_API_KEY="在这里粘贴你的密钥"
export PAPER_SEARCH_MCP_CORE_API_KEY="在这里粘贴你的密钥"
export PAPER_SEARCH_MCP_OPENALEX_API_KEY="在这里粘贴你的密钥"
```

**检查是否成功**（在新终端中）：Windows 输入 `echo $env:PAPER_SEARCH_MCP_CORE_API_KEY`，Mac 输入 `echo $PAPER_SEARCH_MCP_CORE_API_KEY`，
应该会显示你的密钥。然后在 Claude Code 或 Codex 中输入 `/mcp`。

## 本仓库里有什么

本仓库**本身就是**项目模板：一份副本 = 一篇论文。

```
agentic-research/
├── README.md                 英文说明                   README.zh-CN.md  本文件
├── AGENTS.md                 所有助手都会读取的规则（填写方括号 [ ] 中的内容）
├── CLAUDE.md                 让 Claude Code 加载 AGENTS.md
├── .mcp.json                 Claude Code 的插件设置（不含密钥）
├── .codex/config.toml        Codex 的插件设置（不含密钥）
├── .claude/skills/           给 Claude Code 的 4 个科研技能
├── .agents/skills/           给 Codex 的同样 4 个技能
├── .gitignore  .env.example  防止密钥和原始数据被上传；列出密钥的名称
├── setup-guides/             分步指南 01–08（英文）和设置示例
├── docs/plans/  status/      研究计划，以及每个任务一份进度文件
├── docs/protocol/            在看结果之前冻结的分析方案
├── docs/literature/          检索记录、已核实的参考文献、创新性检查
├── docs/reports/             结果报告，每个都由脚本生成
└── paper/ data/ analysis/ references/ figures/
```

分步指南特意放在项目里：AI 助手可以读取它们，所以你可以直接问助手，例如：*“请帮我完成 setup-guides/01-install.md 的第 3 步。”*

以点开头的文件和文件夹（如 `.mcp.json`、`.codex`、`.claude`、`.agents`）在有些电脑上是隐藏的。
Windows 文件资源管理器：查看 → 显示 → 隐藏的项目。Mac 访达：按 Cmd + Shift + .（句点）。

## 什么是 “.md” 文件？

以 **.md**（Markdown）结尾的文件就是普通的文本文件，不需要特别的软件：

- **Windows：** 右键点击文件 → 打开方式 → **记事本**。
- **Mac：** 右键点击文件 → 打开方式 → **文本编辑**。
- **最简单：** 让助手帮你，例如：*“和我一起填写 AGENTS.md，每次只问我一个问题。”*

行首的 `#` 表示标题，`-` 表示列表项，两个 `**` 之间的文字是粗体。就这么简单。

## 典型的科研流程

| 阶段 | 做什么 | 留下的文件 |
|---|---|---|
| 1. 研究问题 | 填写 AGENTS.md | `AGENTS.md` |
| 2. 计划 | 划分阶段和任务（工作包） | `docs/plans/01-study-plan.md` |
| 3. 文献 | 检索、筛选、打开原文、存入 Zotero（`literature-review`） | `docs/literature/search-log.md`、`verified-references.md` |
| 4. 创新性 | 找出最相近的论文并全部阅读（`novelty-check`） | `docs/literature/novelty-check.md` |
| 5. 研究方案 | 冻结假设和分析计划；提交（commit）并打标签（tag） | `docs/protocol/protocol.md` |
| 6. 分析 | 用脚本分析，绝不手工改数据 | `analysis/`、`docs/reports/results.md`、`figures/` |
| 7. 写作 | 逐节撰写（`write-section`） | `paper/` |
| 8. 投稿 | 核查每一条引用（`citation-check`），最后检查 | `docs/reports/citation-check-*.md` |

## 用到的工具及来源

| 工具 | 用途 | 官方页面 |
|---|---|---|
| Claude Code | AI 助手（Claude 桌面应用的 Code 标签页） | https://code.claude.com/docs/en/setup |
| Codex | AI 助手（ChatGPT 桌面应用） | https://learn.chatgpt.com/docs/quickstart |
| GitHub Desktop / Git | 版本管理、私有在线备份、审阅修改 | https://github.com/apps/desktop · https://git-scm.com |
| uv | 运行插件 | https://docs.astral.sh/uv/ |
| paper-search-mcp | 22 个学术数据库，MIT 许可 | https://github.com/openags/paper-search-mcp |
| Zotero 10 | 文献管理（界面可设为简体中文） | https://www.zotero.org |
| Better BibTeX | 稳定的引用键，自动导出 .bib 文件，MIT 许可 | https://retorque.re/zotero-better-bibtex/ |
| 茉莉花 Jasminum | 在 Zotero 中支持知网等中文数据库，AGPL-3.0 | https://github.com/l0o0/jasminum |
| zotero-mcp（54yyyu） | 让助手读取你的 Zotero 文献库，MIT 许可 | https://github.com/54yyyu/zotero-mcp |
| Claude in Chrome | Claude 的浏览器扩展 | https://claude.com/chrome |
| Google Workspace 连接器 | 在 Claude 中使用 Drive、Gmail、日历 | https://support.claude.com/en/articles/10166901-use-google-workspace-connectors |
| Anthropic skills | Word、PowerPoint、PDF、Excel、skill-creator（Claude） | https://github.com/anthropics/skills |
| AGENTS.md | AI 规则文件的开放格式 | https://agents.md |

## 安全提示

- 本工具包**不包含任何真实的密钥、令牌、邮箱或个人信息**。分享你的项目时也请保持这一点。
- 安装别人提供的插件、技能或扩展之前，先阅读它的页面和许可证：它会给你的助手增加新的能力。
- 论文检索插件带有 Sci-Hub 选项，默认关闭，请保持关闭。
- 访谈和问卷数据在交给任何 AI 之前先做匿名化处理，并遵守你的伦理审批要求。
- 让助手**起草**；发送、提交和删除由你自己来做。
- 查看目标期刊关于使用 AI 的规定，并按要求声明。

## 许可

本工具包中的指南、模板和技能采用 **知识共享 署名-非商业性使用 4.0 国际许可协议（CC BY-NC 4.0）**：
可以在任何非商业用途（学习、研究、教学）中免费使用、分享和修改，但需注明出处。https://creativecommons.org/licenses/by-nc/4.0/deed.zh-hans

工具包中提到的各个工具保留各自的许可证（见上表）。

本工具包的在线地址：https://github.com/samrand96/agentic-research
