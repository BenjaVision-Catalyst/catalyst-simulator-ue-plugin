# Catalyst Simulator Plugin

CatalystSimulatorPlugin is the shared Unreal Engine simulation binding and data
management layer. This repository is registered in the Catalyst workspace at
`Simulation/catalyst-simulator-ue-plugin`. Implementation is planned; no working
plugin descriptor, runtime module or engine build is claimed yet.

## Responsibility

- Consume the Runtime Simulation service through CatalystConnect, preserving the
  same client endpoint for GemStone, GT and external simulation backends.
- Manage accepted entity projections, subscriptions/queries/commands, stable IDs,
  revisions/generations, bounded caches and UE-world lifetime.
- Provide common interpolation, Mass/instance adapters, pooled Actors and global
  frame/memory/representation budgets.
- Expose world-scoped domain presentation providers and generic descriptor types.

The plugin does not own ecosystem rules or choose species meshes, textures,
materials or animation. CatalystEcosystemPlugin supplies that content and policy
through these shared APIs. The Simulator plugin must load without ecosystem
content, and must not create one network connection or UObject cache per creature.

## Dependencies and planned structure

Use the existing CatalystFoundation/CatalystConnect UE family conventions.
Separate the base projection module from optional Mass/direct-instance adapters;
editor and automation modules remain outside packaged runtime dependencies.
The GameInstance owns the connection and each World owns its projection mappings.
Start desktop/console qualification with an isolated pinned-engine host.

The portable kernel/service lives in
[catalyst-simulator](https://github.com/BenjaVision-Catalyst/catalyst-simulator).
The domain presentation consumer lives in
[catalyst-ecosystem-ue-plugin](https://github.com/BenjaVision-Catalyst/catalyst-ecosystem-ue-plugin).
See the shared [component boundaries](https://github.com/BenjaVision-Catalyst/catalyst-simulator/blob/main/docs/Component-Boundaries.md),
[implementation plan](https://github.com/BenjaVisionPro/catalyst-workspace/blob/main/Simulation/Catalyst-Simulation-Implementation-Plan.md)
and [UE projection research](https://github.com/BenjaVisionPro/catalyst-workspace/blob/main/Simulation/UE-Projection-Research-and-Design.md).
