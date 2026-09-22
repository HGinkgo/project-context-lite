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

Copy this directory into your Codex skills directory, or install it from this repository as a local skill. Then invoke it for a project that needs persistent context.

## Suggested project files

Copy only what the project needs from `templates/` into `<project>/.agent/`.
