# r3f-audit

`r3f-audit` is an llm skill for auditing React Three Fiber and Three.js code. It focuses on performance, GPU cost, render-loop behavior, memory pressure, and architectural issues that show up in real-time 3D apps.

# Why?

React and real-time 3D systems want different things. React is comfortable with re-renders and immutable updates; Three.js usually needs stable objects, explicit mutation in hot paths, and minimal per-frame work. This skill exists to catch those conflicts early and turn them into concrete, high-impact fixes.
Run this skill audit your codebase and ensure you're avoiding footguns.

## A note
This covers a lot of ground but I'm sure a lot could be added to enhance and optimize the skill. Feel free to update and share.

## How To Use It

Just call the /skill from your favourite llm cli/interface.
Use this skill when you want Codex to audit a Three.js or React Three Fiber codebase.

Example:

```text
Use the r3f-audit skill to review this scene for performance problems.
```

For mobile-focused reviews, include:

```text
mode: mobile
```

The skill definition lives in [SKILL.md](/home/buche/code/llm_skill/r3f-audit-skill/SKILL.md), with supporting heuristics in [checklist.md](/home/buche/code/llm_skill/r3f-audit-skill/checklist.md) and [mobile.md](/home/buche/code/llm_skill/r3f-audit-skill/mobile.md).




