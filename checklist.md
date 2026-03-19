# R3F Audit Checklist

Apply these heuristics aggressively.

---

## React Pressure

- frequent re-renders of large scene trees
- inline arrays/objects/functions in JSX
- state updates affecting many nodes
- context updates across scene
- animation stored in React state

---

## Allocation Churn

- new THREE objects in render
- new objects in useFrame
- recreating materials/geometries
- cloning assets repeatedly

---

## Frame Loop Abuse

- many useFrame hooks
- per-frame allocations
- redundant math per object
- state updates inside frame loop

---

## Resource Management

- missing disposal
- remounting heavy objects
- unstable args arrays
- loaders triggered repeatedly

---

## Scene Graph Cost

- too many meshes
- no instancing
- too many materials
- deep hierarchies updating frequently

---

## Lighting / Shadows

- too many lights
- too many shadow casters
- large shadow maps

---

## Materials / Shaders

- excessive PBR usage
- many unique materials
- transparency overuse
- shader recompilation triggers

---

## R3F Anti-patterns

- unstable keys
- remounting to reset state
- declarative updates for fast transforms
- frameloop misuse

---

## Assets

- large GLTFs unoptimized
- repeated loading
- large textures
- no compression

---

## Interaction

- excessive raycasting
- per-frame interaction logic
- too many interactive objects
