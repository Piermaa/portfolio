# Minigolf – Physics-Driven 2D Vertical Slice

**Engine:** Unity  
**Language:** C#  
**Genre:** Top-down 2D Minigolf  
**Project Type:** Vertical Slice  
**Focus:** Physics simulation, trajectory prediction, gameplay feel

## Overview

This project is a **vertical slice of a top-down 2D minigolf game**, built to validate core gameplay systems before full production.

The main design goal was to ensure that **player intention, visual feedback, and physical outcome are fully aligned**. Every system prioritizes predictability, consistency, and player trust over visual complexity.

## My Role 
**Lead / Main Programmer**
Worked closely with a designers, owning most gameplay, systems, tools, and optimization work.

## Core Systems I Devloped

### Gameplay & Physics
- Designed and implemented physics-based movement refined for responsiveness and player control.
- Implemented two main gameplay modes:
  - **Free Roam Mode** for exploration and traversal.
  - **Golf Mode**, enforcing golf rules (shot-only movement, cooldowns, ball must stop before next hit).
- Implemented shot trajectory prediction that: 
	- Calculates rebounds and distance visualization.
	- Considers height changes during shots, modifing the layer mask to look for obstacles when necessary

<!-- Gif de hoyo de golf -->

### Ability System
- Designed a data-driven ability system using **Scriptable Objects**.
- Centralized **Abilities Manager** handling:
  - Cooldowns
  - Ability blocking
  - Skill cancellation and recasting
  - Communication between abilities and the player controller
- Implemented abilities such as:
  - Grappling hook (anchor-based movement and object manipulation)
  - Destructive dash (breaking walls and moving heavy objects)

<!-- Gif de tuto de hook-->

## Height & Verticality System

One of the main technical challenges was supporting verticality in a 2D top-down game without stacking complex colliders.

- Implemented a custom **Height Manager** handling:
  - Collision layers
  - Sorting layers
  - Renderer configuration
- Supported three height levels (Low / Mid / High).
- Height transitions controlled via directional triggers on ramps.
- Implemented an **airborne state** for high-speed traversal:
  - Visual feedback via sprite offset and dynamic shadow scaling.
  - Correct interaction with drops and cliffs.
- Added event-based notifications for systems that needed to react to height changes.

To improve readability in multi-layer dungeons:
- Implemented a **Layer Manager** that dynamically adjusts saturation and brightness of non-relevant layers based on the player’s current height.

<!-- Gif cambiando de altura en dungeon -->

## World Progression & Map System

- Designed a fully decoupled progression system using **Scriptable Objects** and **Addressables**.
- Map structure:
  - Map → Waypoints → Doors / Holes
- Holes unlock doors indirectly via shared zone IDs.
- Doors and holes do not reference each other directly.
- Player progress stored in JSON and propagated using an observer-style event system.
- Dynamic map UI:
  - Displays holes relative to world position.
  - Combines static data (rewards, descriptions) with player progress (scores, unlocks).

<!-- Gif en el mapa -->

## Performance, Debugging & Tools

- Identified and fixed critical performance issues using Unity Profiler.
- Resolved fatal bugs such as:
  - Event subscriptions inside Update loops
  - Excessive Gizmo rendering causing memory leaks
- Optimized physics by:
  - Correct collision layer matrix configuration
  - Proper Rigidbody setup (static vs dynamic)
- Achieved stable high framerates (~200 FPS) across most of the game.

Built internal tools to speed up iteration:
- Progress reset tools for testing first-time player scenarios.
- Position and state debug utilities.
- On-screen debug panel displaying active states and effects.


## Additional Systems

- Puzzle framework:
  - Levers (directional, timed)
  - Keys and locked doors
  - Movable objects affected by physics and abilities
- Boss fight with multiple phases and code-driven animations (coroutines used due to missing art assets).
- Water detection and safe-position respawn system.
- Collectible system inspired by fragment-based health upgrades.
- Simple enemy obstacles acting as physical hazards.
- FMOD-based audio integration with surface-dependent feedback.
- Player feedback improvements:
  - Squash and stretch animations
  - Particle triggers
  - Animator Controller with velocity- and direction-based blend trees

<!-- Gif del jefe -->

## Technical Highlights

- Custom verticality system for a 2D top-down game.
- Data-driven abilities with centralized control and minimal coupling.
- Decoupled world progression using observer-style communication.
- Strong focus on performance, tooling, and player feedback.
- Extensive profiling-driven optimization and debugging.

## Vertical Slice Scope

The current slice includes:

- Fully playable minigolf hole
- Shot input and aiming system
- Physics-driven ball movement
- Accurate trajectory preview
- Collision and rebound logic
- Tunable physics parameters for fast iteration

The slice was built to validate **core feel and systems**, not content volume.


## Status

This project is currently a **vertical slice**.  
The core mechanics are validated and ready to be expanded into additional levels, obstacles, and gameplay modifiers.

