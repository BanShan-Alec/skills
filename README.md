<p>
  <a href="https://www.aihero.dev/s/skills-newsletter">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://res.cloudinary.com/total-typescript/image/upload/v1777382277/skills-repo-dark_2x.png">
      <source media="(prefers-color-scheme: light)" srcset="https://res.cloudinary.com/total-typescript/image/upload/v1777382277/skill-repo-light_2x.png">
      <img alt="Skills" src="https://res.cloudinary.com/total-typescript/image/upload/v1777382277/skill-repo-light_2x.png" width="369">
    </picture>
  </a>
</p>

# 给真实工程师的技能

> 这是 [mattpocock/skills](https://github.com/mattpocock/skills) 的个人 fork。改动见[这个 fork 有什么不同](#这个-fork-有什么不同)。下面的 GitHub 和 skills.sh 安装命令指向这个 fork；Claude Code 官方 marketplace 仍然安装上游插件。

[![GitHub](https://img.shields.io/badge/GitHub-BanShan--Alec%2Fskills-181717?logo=github)](https://github.com/BanShan-Alec/skills)

我每天用来做真实工程的 agent 技能，不是 vibe coding。

开发真实应用很难。GSD、BMAD、Spec-Kit 这类方法试图通过接管流程来帮忙，但这样做也拿走了你的控制权，让流程里的 bug 更难排查。

这些技能被设计得小、易改、可组合。它们适用于任何模型，基于几十年的工程经验。随便折腾，改成你自己的。玩得开心。

如果你想跟上这些技能的变化，以及我创建的新技能，可以加入我约 6 万名开发者的 newsletter：

[订阅 newsletter](https://www.aihero.dev/s/skills-newsletter)

## 这个 fork 有什么不同

这个 fork 保留上游的纪律，去掉我不用的部分。

| 项目 | 上游 | 这个 fork |
| --- | --- | --- |
| 技能数量 | 39 个：27 个正式发布，8 个 in-progress，4 个 misc | 28 个正式发布 |
| `brainstorming` | 没有 | 面向模糊想法的 user-invoked 前门 |
| 技能描述 | 英文 | 简洁中文，Matt 技能带 `[matt]` 前缀 |
| 文档链接 | `aihero.dev` 绝对外链 | GitHub 上可解析的相对链接 |
| 安装入口 | `mattpocock/skills` | GitHub 和 skills.sh 指向 `BanShan-Alec/skills` |

`brainstorming` 是唯一新增的技能。它保留开放式探索，然后把决策树交给 `grilling`，在满足条件时通过 `domain-modeling` 记录术语和 ADR，停在已经批准的设计上。它不写 design document 或 plan，也没有 visual companion；之后运行 `/to-spec` 和 `/to-tickets`。

`misc/` 和 `in-progress/` 两个 bucket 已删除，插件和文档只覆盖正式发布的技能集。

## 安装（30 秒完成）

插件会自动更新。skills.sh 安装器会把可编辑文件复制到你的项目里，之后由你手动更新。每个 agent 只选一种方式，因为两种都装会让每个技能出现两次。

### 1. 获取技能

<details>
<summary><strong>Claude Code</strong></summary>

```bash
claude plugin install mattpocock-skills@claude-plugins-official
```

默认自动更新。这条路线安装的是官方 marketplace 里的上游插件。要安装这个 fork，请使用下面的 GitHub 或 skills.sh 路线。

</details>

<details>
<summary><strong>Codex</strong></summary>

```bash
codex plugin marketplace add BanShan-Alec/skills
codex plugin add mattpocock-skills@mattpocock
```

启动时自动更新。

</details>

<details>
<summary><strong>GitHub Copilot</strong>（CLI 和 VS Code）</summary>

```bash
copilot plugin marketplace add BanShan-Alec/skills
copilot plugin install mattpocock-skills@mattpocock
```

然后，一次性把下面内容加到 `~/.copilot/settings.json`：

```json
{
  "extraKnownMarketplaces": {
    "mattpocock": { "source": { "source": "github", "repo": "BanShan-Alec/skills" }, "autoUpdate": true }
  }
}
```

在 VS Code 里运行 **Chat: Install Plugin From Source**，输入 `https://github.com/BanShan-Alec/skills`。它每天自动更新。

</details>

<details>
<summary><strong>Gemini CLI</strong>（手动更新）</summary>

```bash
gemini skills install https://github.com/BanShan-Alec/skills.git --path skills/engineering
gemini skills install https://github.com/BanShan-Alec/skills.git --path skills/productivity
```

重新运行这两条命令即可更新。

</details>

<details>
<summary><strong>任何其他 agent，或需要可编辑文件</strong>（手动更新）</summary>

```bash
npx skills@latest add BanShan-Alec/skills -a <agent>  # cursor, opencode, devin, windsurf, amp, pi; omit -a to choose
```

当安装器询问要装哪些技能时，记得包含 `setup-matt-pocock-skills`。更新时运行 `npx skills@latest update`，再运行一次 `add` 来获取新技能。

</details>

### 2. 运行 `/setup-matt-pocock-skills`

在你的 agent 里，每个 repo 运行一次。它会：

- 询问你想使用哪个 issue tracker（GitHub、GitLab、本地文件，或你描述的其他方式）
- 询问你在 triage 工单时使用哪些标签（`/triage` 会用到这些标签）
- 询问你希望把生成的文档保存到哪里

### 3. 搞定，可以开始了。

## 为什么会有这些技能

我做这些技能，是为了修复我在 Claude Code、Codex 和其他 coding agent 上看到的常见失败模式。

### #1：Agent 没有做我想要的

> “没有人确切知道自己想要什么。”
>
> David Thomas & Andrew Hunt，[《程序员修炼之道》](https://www.amazon.co.uk/Pragmatic-Programmer-Anniversary-Journey-Mastery/dp/B0833F1T3V)

**问题**：软件开发里最常见的失败模式是目标不一致。你以为开发者知道你想要什么。然后你看到他做出来的东西，才发现他根本没理解你。

到了 AI 时代，这一点没有变。你和 agent 之间存在沟通鸿沟。修复方式是 **grilling session（追问式会话）**：让 agent 就你正在构建的东西问你详细问题。

**修复方式**是使用：

- [`/grill-me`](./skills/productivity/grill-me/SKILL.md)：用于非代码场景
- [`/grill-with-docs`](./skills/engineering/grill-with-docs/SKILL.md)：和 [`/grill-me`](./skills/productivity/grill-me/SKILL.md) 一样，但额外提供一些东西（见下文）

这是我最受欢迎的技能。它们帮助你在开始前和 agent 对齐，并深入思考要做的改动。每次想做改动时都用它们。

### #2：Agent 太啰嗦

> 有了统一语言，开发者之间的对话和代码表达都来自同一个领域模型。
>
> Eric Evans，[《领域驱动设计》](https://www.amazon.co.uk/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215)

**问题**：项目开始时，开发者和他们为之构建软件的人（领域专家）通常说着不同的语言。

我和 agent 之间也有同样的紧张感。Agent 通常被丢进一个项目，然后被要求边做边猜术语。于是本来一个词能说清的事，它要用二十个词。

**修复方式**是建立共享语言。它是一份文档，帮助 agent 解读项目里的行话。

<details>
<summary>
例子
</summary>

这里有一个[词汇表](https://github.com/mattpocock/course-video-manager/blob/076a5a7a182db0fe1e62971dd7a68bcadf010f1c/CONTEXT.md)的例子（在那个固定 commit 里还叫 `CONTEXT.md`，是在技能重命名这套约定之前），来自我的 `course-video-manager` 仓库。哪个更容易读？

- **之前**：“课程某个 section 里的 lesson 被‘实体化’（也就是在文件系统里拿到位置）时会有问题。”
- **之后**：“materialization cascade 有问题。”

这种简洁会在一次次会话里持续带来回报。

</details>

这已经内置在 [`/grill-with-docs`](./skills/engineering/grill-with-docs/SKILL.md) 里。它是一次 grilling session，但会帮助你与 AI 建立共享语言，并把难以解释的决策记录到 ADR 里。

很难解释这有多强大。它可能是这个仓库里最酷的技术。试试看。

> [!TIP]
> 共享语言除了减少啰嗦，还有很多好处：
>
> - **变量、函数和文件命名一致**，都使用共享语言
> - 因此，**代码库对 agent 来说更容易导航**
> - Agent 也会**在思考上花更少的 token**，因为它可以使用更简洁的语言

### #3：代码跑不起来

> “总是迈小步、深思熟虑地前进。反馈速度就是你的速度上限。永远不要接太大的任务。”
>
> David Thomas & Andrew Hunt，[《程序员修炼之道》](https://www.amazon.co.uk/Pragmatic-Programmer-Anniversary-Journey-Mastery/dp/B0833F1T3V)

**问题**：假设你和 agent 已经对要构建的东西达成一致。但如果 agent 仍然产出垃圾呢？

这时候要看你的反馈回路。如果 agent 无法得到代码实际运行效果的反馈，它就是在盲飞。

**修复方式**：你需要常规的一整套反馈回路：静态类型、浏览器访问和自动化测试。

对于自动化测试，red-green-refactor 循环至关重要。也就是 agent 先写一个失败的测试，再修到测试通过。这能给 agent 一致的反馈水平，从而产出好得多的代码。

我做了 **[`/tdd`](./skills/engineering/tdd/SKILL.md) 技能**，可以插进任何项目。它鼓励 red-green-refactor，并在什么是好测试、什么是坏测试上给 agent 很多指导。

调试方面，我还做了 **[`/diagnosing-bugs`](./skills/engineering/diagnosing-bugs/SKILL.md)** 技能，把最佳调试实践包成一个有纪律的循环，按阶段设门。

### #4：我们造了一个泥球

> “每天都要投资于系统的设计。”
>
> Kent Beck，[《解析极限编程》](https://www.amazon.co.uk/Extreme-Programming-Explained-Embrace-Change/dp/0321278658)

> “最好的模块是深的。它们让大量功能通过一个简单接口被访问。”
>
> John Ousterhout，[《软件设计哲学》](https://www.amazon.co.uk/Philosophy-Software-Design-2nd/dp/173210221X)

**问题**：大多数用 agent 构建的应用都很复杂、难以修改。因为 agent 能极大加速编码，它们也会加速软件熵增。代码库以前所未有的速度变复杂。

**修复方式**是一种激进的 AI 开发新思路：关心代码的设计。

这已经内置在这些技能的每一层：

- [`/to-spec`](./skills/engineering/to-spec/SKILL.md) 在创建 spec 之前，会先问你正在碰哪些模块

而且关键的是，[`/improve-codebase-architecture`](./skills/engineering/improve-codebase-architecture/SKILL.md) 会扫描代码库里的加深机会，把候选交给你。我建议每隔几天在代码库上跑一次。它是一次普查，不是救援：在真正老旧的代码库上，它会找到真实候选，但不会替你解开泥团。

### 总结

软件工程基本功比以往任何时候都重要。这些技能是我把这些基本功浓缩成可重复实践的最好尝试，帮你做出职业生涯里最好的应用。玩得开心。

## 参考

这些技能按一个维度划分：谁能调用它们。**User-invoked** 技能只有你输入时才可达（例如 `/grill-me`），职责是编排。**Model-invoked** 技能可以由你调用，也可以在任务匹配时由 agent 自动触达，承载可复用的纪律。User-invoked 技能可以调用 model-invoked 技能，但永远不能调用另一个 user-invoked 技能。

### Engineering

我每天用于代码工作的技能。

**User-invoked**

- **[ask-matt](./skills/engineering/ask-matt/SKILL.md)**：不知道该用哪个技能或流程时，帮你选择。它是本仓库 user-invoked 技能的路由器。
- **[brainstorming](./skills/engineering/brainstorming/SKILL.md)**：在对话中把模糊想法打磨成已批准的设计，然后交给 `/to-spec` 和 `/to-tickets`。
- **[grill-with-docs](./skills/engineering/grill-with-docs/SKILL.md)**：追问式会话，同时构建项目领域模型，打磨术语，并就地更新 `GLOSSARY.md` 和 ADR。
- **[triage](./skills/engineering/triage/SKILL.md)**：让 issue 经过 triage 角色的状态机。
- **[improve-codebase-architecture](./skills/engineering/improve-codebase-architecture/SKILL.md)**：扫描代码库里的加深机会，生成可视化 HTML 报告，再对选中的机会进行追问。
- **[setup-matt-pocock-skills](./skills/engineering/setup-matt-pocock-skills/SKILL.md)**：为工程技能配置仓库（issue tracker、triage 标签、领域文档布局）。每个 repo 使用其他工程技能前运行一次。
- **[to-spec](./skills/engineering/to-spec/SKILL.md)**：把当前对话整理成 spec 并发布到 issue tracker。不再访谈，只归纳已讨论的内容。
- **[to-tickets](./skills/engineering/to-tickets/SKILL.md)**：把计划、spec 或对话拆成一组 tracer-bullet 工单，每个都声明阻塞关系，可写成本地文件，也可在真实 tracker 上使用原生阻塞链接。
- **[implement](./skills/engineering/implement/SKILL.md)**：按 spec 或工单构建工作，在预先约定的 seam 上驱动 `/tdd`，提交前用 `/code-review` 收尾。
- **[implement-spec](./skills/engineering/implement-spec/SKILL.md)**：在一个 integration branch 上实现整个 spec。把工单当成任务图，在就绪 frontier 上并行运行 implementer subagent，最大化并发，最后用 `/code-review` 收尾。
- **[wayfinder](./skills/engineering/wayfinder/SKILL.md)**：把超过一次 agent 会话容量的大块工作规划成 issue tracker 上的决策工单共享地图，逐个解决，直到通往目的地的路线清晰。
- **[retro](./skills/engineering/retro/SKILL.md)**：在一次会话后提出改进 coding agent 环境的建议（导航、自动化检查、编码规范、steering 文件、工具），按严重程度排序。

**Model-invoked**

- **[prototype](./skills/engineering/prototype/SKILL.md)**：构建一次性原型来回答设计问题：要么是单个可分享的 HTML 文件，用于状态/逻辑问题；要么是在一个路由里可切换的多个截然不同的 UI 变体。
- **[diagnosing-bugs](./skills/engineering/diagnosing-bugs/SKILL.md)**：针对难 bug 和性能回归的有纪律诊断循环：建立一个能对这个 bug 变红的反馈回路 → 最小化 → 假设 → 插桩 → 修复 → 回归测试。
- **[research](./skills/engineering/research/SKILL.md)**：针对高可信一手资料调查一个问题，并把发现整理成带引用的 Markdown 文件放进 repo，作为后台 agent 运行。
- **[tdd](./skills/engineering/tdd/SKILL.md)**：测试驱动开发，red-green-refactor 循环。一次一个纵向切片地构建功能或修 bug。
- **[domain-modeling](./skills/engineering/domain-modeling/SKILL.md)**：主动构建并打磨项目领域模型：对照 glossary 挑战术语，用边界场景压力测试，并就地更新 `GLOSSARY.md` 和 ADR。
- **[codebase-design](./skills/engineering/codebase-design/SKILL.md)**：设计深模块的共享纪律和词汇：大量行为藏在小接口后面，放在干净的 seam 上，通过接口可测试。
- **[code-review](./skills/engineering/code-review/SKILL.md)**：从固定点开始对 diff 做双轴 review：**Standards**（是否遵守 repo 编码规范，以及 Fowler smell 基线？）和 **Spec**（是否忠实实现来源 issue/spec？），用并行 subagent 运行，互不污染。
- **[pr](./skills/engineering/pr/SKILL.md)**：Pull Request 正文应该长什么样：用最小的可视化摘要说清改动，附上改动前后可工作的证据，并给出 merge 风险判断（单向门/双向门，加上 blast radius）。
- **[wizard](./skills/engineering/wizard/SKILL.md)**：生成交互式 bash 向导，带人完成只有人能做的步骤：配置基础设施、设置凭据或 CI secret、走陌生的第三方后台、做一次性迁移或切换。

### Productivity

通用工作流工具，不针对代码。

**User-invoked**

- **[grill-me](./skills/productivity/grill-me/SKILL.md)**：围绕计划或设计被持续追问，直到设计树的每个分支都解决。
- **[handoff](./skills/productivity/handoff/SKILL.md)**：把当前对话压缩成交接文档，让另一个 agent 继续工作。
- **[teach](./skills/productivity/teach/SKILL.md)**：跨多次会话教用户一个新技能或概念，用当前目录作为有状态的教学校验空间。
- **[to-questionnaire](./skills/productivity/to-questionnaire/SKILL.md)**：把一个你无法独自回答的决策变成 Markdown 问卷，交给唯一能回答的人，可异步填写，也可在会议上一起填。它追问的是“发送”（给谁、需要拿回什么），不是主题本身。
- **[wait-what](./skills/productivity/wait-what/SKILL.md)**：当一条消息没听懂时立刻使用。Agent 会用你缺失的上下文、用简单英语、使用你的 `GLOSSARY.md` 词汇重新讲一遍。

**Model-invoked**

- **[grilling](./skills/productivity/grilling/SKILL.md)**：围绕计划、决策或想法持续追问，直到设计树的每个分支都解决。它是 `grill-me`、`grill-with-docs`、`triage`、`wayfinder` 和 `improve-codebase-architecture` 背后的可复用访谈原语。
- **[writing-for-agents](./skills/productivity/writing-for-agents/SKILL.md)**：编写给 agent 看的文档：技能、AGENTS.md/CLAUDE.md，以及任何通过指针被 agent 读取的文档。
