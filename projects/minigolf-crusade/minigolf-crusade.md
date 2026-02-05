# Minigolf – Physics-Driven 2D Vertical Slice

**Engine:** Unity  
**Language:** C#  
**Genre:** Top-down 2D Minigolf  
**Project Type:** Vertical Slice  
**Focus:** Physics simulation, trajectory prediction, gameplay feel

## Overview

This project is a **vertical slice of a top-down 2D minigolf game**, built to validate core gameplay systems before full production.

The main design goal was to ensure that **player intention, visual feedback, and physical outcome are fully aligned**. Every system prioritizes predictability, consistency, and player trust over visual complexity.

Rather than relying on approximations or “fake” assists, the game uses **real physics simulation** both for gameplay and for player-facing previews.

## Core Gameplay Systems

### Physics-Based Trajectory Prediction

Before taking a shot, the player sees a **predicted trajectory** rendered as a sequence of points.

Key characteristics:

- The preview uses the **same physics rules as the actual ball**
- No raycast shortcuts or analytical approximations
- Step-by-step simulation using fixed time steps
- Supports:
  - Linear drag
  - Multiple rebounds
  - Configurable bounciness (currently 75%)
- Prediction length adapts dynamically based on shot strength

This guarantees that the preview accurately reflects what will happen once the ball is released.

### Deterministic Simulation

Both preview and gameplay rely on deterministic logic:

- Fixed timestep simulation
- Identical parameters for preview and real physics
- Consistent behavior across edge cases (shallow angles, corners, multi-bounce shots)

Any tweak to physics values immediately affects **both systems**, making iteration fast and reliable.

### Trajectory Visualization

![Trajectory Prediction](media/Hook_Skill_Exploration.gif)

The trajectory visualization was designed for clarity:

- Points are evenly distributed along the simulated path
- Spacing adapts based on velocity and distance
- Visualization stops once kinetic energy falls below a threshold
- Designed to avoid clutter while still showing:
  - Direction
  - Power
  - Rebounds

The goal is to communicate information, not spectacle.

### Collision & Rebound Handling

Rebounds are calculated using:

- Collision normals
- Energy loss through restitution
- Directional reflection consistent with Unity’s physics model

This allows players to plan and execute complex bank shots with confidence.

## Vertical Slice Scope

The current slice includes:

- Fully playable minigolf hole
- Shot input and aiming system
- Physics-driven ball movement
- Accurate trajectory preview
- Collision and rebound logic
- Tunable physics parameters for fast iteration

The slice was built to validate **core feel and systems**, not content volume.

## Technical Focus

This project emphasizes:

- Clean separation between simulation and visualization
- Reusable physics logic shared by multiple systems
- Predictable gameplay outcomes
- Systems designed for scalability (additional surfaces, hazards, modifiers)

## Status

This project is currently a **vertical slice**.  
The core mechanics are validated and ready to be expanded into additional levels, obstacles, and gameplay modifiers.

