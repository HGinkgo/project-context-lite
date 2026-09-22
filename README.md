# project-context-lite

A lightweight Codex skill for maintaining personal project context without adopting a heavyweight CI or code-review process.

It keeps durable project knowledge in a small `.agent/` directory:

- project background and constraints;
- current state and next action;
- technical decisions;
- benchmark evidence;
- short phase plans.

The skill deliberately uses staged validation. Documentation changes and ordinary edits get only the smallest relevant check. Targeted tests or benchmarks run at milestones, and a broader review is reserved for releases, merges, or resume-ready results.

## Install

Clone this repository into your Codex skills directory:

```powershell
git clone git@github.com:HGinkgo/project-context-lite.git `
  "$env:USERPROFILE\.codex\skills\project-context-lite"
```

Update it later with:

```powershell
git -C "$env:USERPROFILE\.codex\skills\project-context-lite" pull
```

## Usage

In a project directory, invoke the skill explicitly:

```text
$project-context-lite
请读取当前项目，初始化轻量项目上下文。
只创建必要的 .agent 文件，不要运行全量测试。
```

For ordinary work:

```text
$project-context-lite
根据当前 STATE.md，继续推进唯一主线。先分析，不要直接大规模修改。
```

At a milestone:

```text
$project-context-lite
记录本阶段的技术决策和 benchmark 结果，只运行与本阶段相关的验证。
```

Before writing a resume entry:

```text
$project-context-lite
根据已验证的 STATE.md、DECISIONS.md 和 BENCHMARKS.md，
整理这个项目可以写进简历的真实工作点，不编造数据。
```

The skill is a project memory and scope-control tool, not an automatic test framework. It does not require a full test suite after every edit or commit.

## Suggested project files

Copy only what the project needs from `templates/` into `<project>/.agent/`.

Typical files are:

```text
.agent/
├── CONTEXT.md
├── STATE.md
├── PLAN.md
├── DECISIONS.md
├── BENCHMARKS.md
└── TODO.md
```

Small projects may use only `CONTEXT.md` and `STATE.md`.
