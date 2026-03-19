# Mobile Audit Extension

Activated when:
`mode: mobile`

---

## Mobile Constraints

Assume:

- weak GPU
- thermal throttling
- high overdraw cost
- limited memory bandwidth
- touch input
- unstable browser performance

Bias toward:

- fewer draw calls
- simpler shaders
- minimal overdraw
- low memory usage

---

## Mobile Checks

### Draw Calls

Target: ~50–200 max  
Flag anything exceeding this.

---

### Overdraw

- transparent materials
- stacked layers
- particles

Critical issue on mobile.

---

### Lighting

- max 1 shadow light
- avoid dynamic shadows

---

### Shaders

- avoid heavy PBR
- reduce fullscreen effects

---

### Textures

- large textures
- no compression

---

### Geometry

- high poly meshes
- no LOD

---

### Frame Loop

- heavy CPU usage
- redundant updates

---

### React Cost

- re-renders amplified on mobile CPUs

---

### Touch

- hover logic
- excessive raycasting

---

### DPR / Resolution

- high DPR usage
- no scaling strategy

---

### Frameloop

- always rendering static scenes

---

## Severity Adjustment

Escalate:

- draw calls
- overdraw
- shadows
- frame loop cost
- React pressure

---

## Required Output Section

### Mobile Risk Summary

- GPU-bound / CPU-bound / memory-bound

### Mobile Top Fixes

### Mobile Red Flags

---

## Hard Rules

- reject desktop assumptions
- prefer aggressive simplification
- assume mid/low-tier device
