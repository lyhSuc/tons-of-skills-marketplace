---
name: mindmap-craft
description: '把大材料做成你能闭卷讲出来、能亲手改、能拿去干活的思维导图。Build mind maps you can retell, edit, and use: a workflow skill that turns large, messy material (research, source code, documentation, lecture notes) into a layered mind map that works as your thinking layer. Skeleton first, one branch at a time, keywords chosen by the human as retrieval cues, and a closed-book retell test before the map counts as done. Use when learning a new domain, digesting a large document set, or preparing a serious document (spec, report, PRD) that must not be written straight from raw notes. Triggers on: 思维导图, 导图, 整理思路, mind map, mindmap, organize my thinking, study map, knowledge map.'
allowed-tools: Read, Write, Edit, Bash(cmd:*), Grep
version: 1.0.0
license: MIT
author: kral
tags:
- learning
- knowledge-management
- visualization
compatibility: Designed for Claude Code and other Agent Skills hosts
---

# 思维导图 · 思考组织工作流（mindmap-craft）

（中文版在前，English version below.）

## 想法

市面上的导图工具把导图当产出：给一个想法，吐一张图。这个 skill 反过来，导图是思考的正本：一张活的、分层的图，主人能闭卷讲出来，能亲手改，能拿它去写真正的文档。

分工由这个区别定死：

- AI 负责组装：备齐材料、按结构切分、搭分支、核对事实。
- 人只做两件不可外包的事：选关键词，验收。

关键词是提取线索。线索要起作用，里面得有本人自己的编码。这一点有研究撑着：编码特异性（Tulving & Thomson, 1973）说提取线索和当初编码时的情境越像，记得越牢；提取练习的研究（Adesope et al., 2017；Karpicke & Blunt, 2011）说主动回忆比反复看图记得牢。AI 把结论压成一个短语当标题，看着整齐，轮到你提取时唤不起任何东西。所以关键词只有两个合法来源：材料里的原词，或者你亲手选定的词。其他写法只能当内容，不能升成标题。

一张图过三条才算完成：

- 能讲：只看骨架层（主题＋关键词），闭卷把全程复述出来。
- 能改：你能直接编辑、增删、标记，不用等 AI 重排。
- 能用：能从图里投影出至少一个真实交付物（文档、表格、讲解稿）。

## 什么时候用

- 从一手材料学一个陌生系统、代码库或领域。
- 把一大堆调研材料消化掉，变成真记住的东西。
- 写重要文档之前（规格、报告、PRD）：文档不许从原始材料直出，先入图、先过复述验收。

## 工序

1. **备全**：先把一手材料收齐（原文、源码、官方文档）。材料不全不开工。没核实的项单独标出来，不许抹平。
2. **分解**：按材料自己的结构切（机制的步骤、对象、阶段），不按篇幅切。每一块都要能回答：它在全局里是什么位置。
3. **组织**：骨架先行、逐格摸索、最后蒸馏。开图先把全部一级分支一次立齐，哪怕多数是空的，每支标状态（骨架／摸索中／已讲／已通）。然后一格一格填，一格封口再下一格。关键词在一格学完、复述之前才长出来，骨架阶段不预制。AI 给候选并按该格的结构点对账，选定由人。全部格子填满并逐格复述过线之后，把图蒸馏回一层总述，只看总述也能讲全程。薄、厚、再薄：蒸馏不回去的厚，只是收藏，不是学会。
4. **语言**：节点用你自己的话写，术语保留原名。图里出现的每个术语，在它的节点下挂一句人话解释。
5. **验收与投影**：交付前 AI 先自查四项（结构完整、关键词来源合法、关键事实回源对账、密度合规）。验收就是闭卷复述：讲不出的支，展开细行补，错处当场改图。验收没过，不许往下走。过了，才把图里的小块投影成展示块，再整合成正式文档。

这条线是螺旋，不是直线：复述和真实使用会撞出新问题，新问题回到第 1 步重新入图。

## 制作规范

### 结构

- 一图一主题。四层封顶：L0 主题，L1 关键词，L2 一句解释，L3 延伸（例子、反例、标本指针）。再深就拆子图回挂。
- 一级分支 3 到 7 个，优选 3 到 5。每支内顺序固定：关键词（就是标题本身）、一句总述、解释、延伸。总述层要能独立复述。

### 关键词

- 关键词就是分支标题，不另设一条「关键词」支。一支实在需要多个词，词组放在本支最前面。
- 一支一个词或一个名词短语。名词优先，讲机制的用动词短语。
- 能具体不抽象。抽象词的下一层必须挂一个具体例子。
- 用学习当时在场的原词，不事后改名美化。改名要连问题库里的对应条目一起改。
- 来源只有两个合法出处，见「想法」一节。AI 事后归纳的压缩语只能当内容点。

### 节点写法

- 一个节点只装一件事。标题层不许出现完整句子，解释层只许一句话，而且得是人话。
- 先解释，后例子：L2 写定义和机制，L3 才放例子、反例和指针。
- 标本（源码、长引用）不进图，只放指针：文件名加行号。

### 密度与视觉

- 一个节点下子节点超过 7 个，先分组再挂，不许平铺。
- 一支一色，只用来编码分组。关系边上标动词或条件词（因果、触发、条件）；纯从属关系不标。

### 复习

- 复习先只看 L0 到 L1，逐支闭卷讲。讲不出的再展开那一支的 L2、L3。
- 每周至少一次，从空白重画骨架层，和原图对差。差处就是未关账项。
- 复述中发现错，当场改图，并在问题库对应条目标注。图和问题库同词同名，互为索引。

## 一支合格的样子

- 关键词：failOnStartupError
  - 总述：连接失败时，是降级还是整插件失败的总开关
  - 解释：默认 false 是降级（插件照常激活，只是没工具）；true 是连不上直接抛错，落 FAILED
  - 延伸：标本指针，备料的连接配置一节；反例：评审时把它说成「重试开关」就是错

## 人留在哪些点上

固定点只有两个：

1. 选关键词（每格学完、复述前）。几秒钟的事，是唯一不能外包的认知动作。
2. 验收（每张图）。闭卷复述过不过线、对外成品拍不拍板，由人定。

外加一个事件型纠正点：人任何时候发现问题，当场纠正，纠正写回工序本身。同类纠正出现第二次，改的是工序，不是单个产物。其余环节（备全、分解、搭图、自查、投影）全归 AI，不拿中间形态回来反复确认。

## 它不是什么

它不是一键生成器。开会要一张快速对齐的草图，生成器更快，但那种图过一周就废了，因为里面没有你的编码。它也不是笔记格式。笔记是输入（第 1 步的材料）和副产品（与图同词同名的问题库），图是夹在中间、让两头都能用的那一层。

---

# Mindmap Craft (English version)

## The idea

Most mind-map tools treat the map as an output: feed in an idea, get back a diagram. This skill treats the map as thinking infrastructure: a living, layered structure that its owner can retell from memory, edit by hand, and build real documents on.

That difference decides who does what:

- The AI assembles. Gathering material, cutting it along its natural structure, drafting branches, checking facts: all of that is the agent's job.
- The human chooses the keywords and accepts the result. A keyword is a retrieval cue. Research on encoding specificity (Tulving & Thomson, 1973) and the testing effect (Adesope et al., 2017; Karpicke & Blunt, 2011) says a cue only works if your own encoding is in it. A keyword the AI invents by compressing a conclusion looks tidy and recalls nothing. So keywords have exactly two legal sources: the material's own terms, or words the human picks. Everything else stays as content and never becomes a title.

A map is done when its owner passes three tests: can retell it (closed-book, from the skeleton layer only), can edit it (directly, without asking the AI to reshuffle), can use it (project at least one real deliverable out of it).

## When to use

- Learning an unfamiliar system, codebase, or domain from primary sources
- Digesting a large research corpus into something you actually retain
- Preparing a high-stakes document (spec, report, PRD): the document is never written straight from raw material; it goes through the map and the retell test first

## The workflow

1. **Gather completely.** Collect the full primary material first (original texts, source code, first-party docs). No structuring on partial material. Mark unverified items explicitly instead of smoothing them over.
2. **Cut along the natural structure.** Decompose by the material's own joints (mechanism steps, objects, phases), never by length. Every piece must answer: where does this sit in the whole?
3. **Organize: skeleton first, then cell by cell.** Lay out the whole frame in one pass: the topic plus all first-level branches, even if most are still empty, each marked with its state (skeleton, exploring, explained, passed). Then fill one branch at a time and close it before moving on. Keywords are born after a cell is understood, right before its retell test, never pre-fabricated during the skeleton stage. The agent proposes candidates checked against the cell's structural points; the human picks or renames. When every cell is filled and retold, distill the map back to a summary layer you can retell in full. Thin, thick, thin again: if it cannot be distilled, it was collecting, not learning.
4. **Language.** Node text in the owner's plain words; original technical terms keep their original names. Every term appearing in the map gets a one-line plain-language gloss under its node.
5. **Accept, then project.** The agent self-checks before delivery: structure complete, keyword sources legal, key facts traced back to sources, density within limits. The human accepts by retelling closed-book from topic and keywords only. Failed branches get local fixes, never a full redo. Only after acceptance is the map projected into deliverables (tables, diagrams, documents).

The pipeline is a spiral, not a line: retelling and real-world use surface new questions, which re-enter at step 1.

## Map rules

### Structure

- One map, one topic. Four layers max: L0 topic, L1 keyword, L2 one-sentence explanation, L3 extensions (examples, counterexamples, pointers to sources). Deeper than that: split into a sub-map and link back.
- 3 to 7 first-level branches (prefer 3 to 5). Inside a branch, fixed order: keyword (the title itself), one-line summary, explanation, extensions. The summary layer must be retellable on its own.

### Keywords

- The keyword is the branch title; there is no separate "keywords" branch. A branch that truly needs several words puts the word group first.
- One word or one noun phrase per branch; nouns preferred, verb phrases for mechanisms.
- Concrete over abstract; an abstract keyword must hang a concrete example below it.
- Keywords keep the wording used when the material was learned. Renaming a keyword means renaming it in the linked question log too (encoding specificity).
- Legal sources only: the material's own terms, or the human's own pick. AI-compressed summary phrases are content, never titles.

### Nodes

- One node, one thing. No full sentences in the title layer; exactly one sentence in the explanation layer, in plain language.
- Explanation before examples: L2 defines and explains the mechanism; L3 holds examples, counterexamples, and source pointers (file plus line), never the sources themselves.

### Density and visuals

- More than 7 children under one node: group first, then hang. No flat lists.
- One color per branch, encoding grouping only. Edge labels carry verbs or conditions for causal or trigger relations; plain containment stays unlabeled.

### Review

- Review starts at L0 and L1 only: retell each branch closed-book; expand only the branches that fail.
- Weekly: redraw the skeleton layer from blank and diff against the map. The diff is your open-items list.
- The map is alive: an error found while retelling is fixed in the map on the spot, and noted in the linked question log. Map and log share words and names; each indexes the other.

## Worked example (one well-formed branch)

- **failOnStartupError**
  - Summary: the master switch between "degrade" and "fail the whole plugin" when a connection cannot be established
  - Explanation: default `false` means degrade (the plugin activates, its tools are simply absent); `true` means throw on connect failure and land in FAILED state
  - Extension: source pointer, setup notes, connection config section; counterexample: calling it a "retry switch" in review is a miss

## Human-in-the-loop, exactly two fixed points

1. **Keyword selection** (per cell, after learning, before retell). Seconds of human time, the one cognitive act that cannot be outsourced.
2. **Acceptance** (per map). The closed-book retell verdict, and the final say on anything published from the map.

Plus one event-driven point: the human corrects anything, any time, and the correction is written back into this workflow. The same correction twice means the workflow changes, not just the map. Everything else (gathering, cutting, drafting, checking, projecting) belongs to the agent, with no intermediate drafts brought back for approval.

## What this is not

It is not a one-shot diagram generator. If you want a quick visual sketch for a meeting, a generator is faster, and the sketch is useless a week later because none of your encoding is in it. It is not a note-taking format either. Notes are the input (step 1 material) and the by-product (a question log indexed to the map, same words, same names). The map is the layer in between that makes both of them usable.
