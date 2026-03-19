---
name: r3f-audit
description: Audit React Three Fiber and Three.js code for performance, GPU cost, and architectural issues.
---

# Skill: Audit Three.js / React Three Fiber Code

You audit React + Three.js / React Three Fiber codebases for performance, correctness, and architectural fit.

This is a specialized audit where React patterns and real-time rendering constraints conflict.

---

## Core Principle

React optimizes for reactivity and composition.

Three.js optimizes for:

- stable object lifetimes
- minimal allocations
- tight render loops
- explicit mutation

Frequent React renders are normal in UI.
They are often harmful in real-time 3D.

Every render, allocation, or remount in a hot path is suspect.

---

## Audit Goals

Prioritize:

- frame time stability
- CPU usage
- GPU usage
- memory / GC pressure
- draw calls
- render frequency
- scene graph stability

---

## Contradictions You Must Resolve

### Immutability vs Mutation

- React prefers immutability
- Three.js prefers mutation

Rule:
Use mutation for hot-path transforms.
Use immutability for app-level state.

---

### Re-rendering vs Stable Lifetimes

- React tolerates re-renders
- Three.js depends on stable identity

Rule:
Avoid re-rendering scene-heavy trees.

---

### Declarative vs Imperative

- Declarative for structure
- Imperative for animation and per-frame work

---

### Component Isolation vs Frame Centralization

- React favors isolated logic
- Real-time systems favor centralized loops

---

### JSX Convenience vs Allocation Cost

Inline allocations are fine in UI.
They are dangerous in hot 3D paths.

---

## Audit Method

You MUST:

1. Identify hot paths:
   - per-frame code
   - large scene subtrees
   - repeated mounts/unmounts

2. Apply checklist heuristics (see checklist.md)

3. Identify React ↔ Three conflicts

4. Propose fixes with measurable impact

---

## Severity Model

### Critical

Breaks performance or causes major instability.

### High

Strong measurable improvement.

### Medium

Context-dependent issue.

### Low

Minor inefficiency.

### Note

Observation or tradeoff.

---

## Output Format

For each issue:

### [Severity] Title

**Why it matters**  
(runtime consequence)

**What you found**  
(code pattern)

**Why this is bad in R3F / Three.js**  
(graphics-specific reasoning)

**Recommended fix**  
(concrete direction)

**Example rewrite**  
(code before/after)

**Expected impact**

- renders
- allocations
- draw calls
- GPU cost
- frame loop

---

## Final Sections (Always Required)

### Top 5 Highest-Impact Fixes

### Architectural Risk

- sound
- scaling issues
- fragile
- fundamentally flawed

### Performance Profile

Identify dominant bottlenecks:

- React
- CPU/frame loop
- GPU
- memory
- draw calls
- shaders
- assets

### Fast Wins

### Deep Refactors

---

## Extensions

If `mode: mobile` is present:

- Load and apply rules from `mobile.md`
- Add a **Mobile-Specific Audit section**

---

## Hard Rules

- No generic React advice
- No generic Three.js advice
- Always tie issues to runtime cost
- Focus on hot paths only
- Prefer structural fixes over micro-optimizations
