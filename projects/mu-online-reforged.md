# MU Online Reforged

**Engine:** Unreal Engine 5  
**Language:** C++ / Blueprints  
**Genre:** MMORPG (Isometric)  
**Project Type:** Multiplayer Remake  
**Focus:** Systems architecture, scalability, data-driven design, server-side gameplay

## Overview

**MU Online Reforged** is a modern remake of the original *MU Online (1997)*, targeting a gameplay experience close to **Season 3**, rebuilt entirely in **Unreal Engine 5**.

The project focuses on preserving the original game’s formulas, progression, and feel, while modernizing the architecture to support **dedicated servers, scalability, data-driven systems, and modern tooling**.

The game runs fully in **multiplayer with dedicated servers**, with multiple maps instantiated independently and connected through a custom travel system.

## My Role
**Gameplay / Systems Programmer**

I joined the project after initial groundwork was done (MMO Kit adapted to isometric view) and took ownership of designing, implementing, and extending most gameplay systems, tools, and backend-facing logic.

## Core Systems I Developed

## Combat Formulas & Stats

- Implemented character formulas based on the original MU Online:
  - Maximum HP calculation
  - Minimum and maximum damage
  - Skill damage scaling
- Ensured formulas were:
  - Deterministic
  - Server-authoritative
  - Easy to tweak and rebalance

All calculations were designed to be reusable across skills, enemies, and items.

## Skill System

- Designed a **modular, data-driven skill system** using **Data Assets**.
- Skills are composed of **inline instanced behavior objects**, allowing:
  - Rapid skill creation
  - High reusability of logic
  - Minimal duplication
- Common behaviors include:
  - Playing animations
  - Spawning Niagara effects
  - Playing sounds
  - Applying area or single-target damage

This modular approach allowed dozens of skills to be assembled quickly by combining existing modules rather than rewriting logic.

<!-- Video / gif of skill usage -->

## World Travel & Map Instances

- Implemented a **server travel system** for map transitions:
  - Each map instance (Lorencia, Noria, Devias, etc.) runs as its own dedicated server.
  - When a server starts, it registers its port and map data in the database.
  - Players request travel by selecting a destination map.
  - The backend responds with the correct server endpoint.
- Seamless experience for the player:
  - Map selection is done via UI.
  - Connection and travel are handled transparently.

This system supports horizontal scalability and multiple concurrent map instances.

## Crafting System (Chaos Machine)

- Implemented a crafting system inspired by the original **Chaos Machine**:
  - Items are placed into the machine.
  - Recipes are inferred from ingredient combinations.
  - Calculates:
    - Cost
    - Success probability
    - Resulting item
- Designed to be fully data-driven and easily extendable.

<!-- Video / gif of chaos machine -->

## Loot & Drop Calculation

- Implemented a **loot calculation subsystem**:
  - Uses JSON configuration files.
  - Defines:
    - Which enemies drop which items
    - Drop chances per map
    - Multipliers based on enemy type and item category
- Fully decoupled from enemy logic.
- Allows easy customization for:
  - Private servers
  - Custom balance configurations

## Asset & Data Management

- Implemented **Asset Manager** for:
  - Items
  - Skills
  - Enemies
- Ensured controlled loading and memory usage.
- Enabled async asset loading across gameplay systems.

- Implemented **Significance Manager**:
  - Strong culling based on isometric camera perspective.
  - Improved performance in high-entity-density scenarios.

## Performance & Scalability

- Implemented an **Object Pooler** for:
  - Enemies
  - Dropped items
- Reduced runtime allocations and spawn overhead.
- Optimized large scenes by:
  - Converting Static Mesh Actors to **HISM** (Hierarchical Instanced Static Meshes).

## Tools & Pipeline Improvements

Developed multiple internal tools to speed up production:

- Mass renaming tool.
- Item and enemy import tools:
  - Converted original MU server `.txt` files into Unreal Data Assets.
- Map visualization tool:
  - Toolbar button to snap the editor view to isometric perspective.
- Map configuration via JSON:
  - Enables custom server setups without rebuilding the project.

## Animation & Asset Integration

- Retargeted Unreal Engine 5 animations to the original MU skeleton.
- Imported and integrated assets from a different engine into Unreal.
- Implemented materials for:
  - Landscapes
  - Enemies
  - Weapons and armors

## UI Improvements

- Replaced a custom drag-and-drop system with **Unreal’s native Drag & Drop**:
  - Reduced bugs
  - Improved stability
  - Simplified maintenance
- Improved inventory and interaction workflows.

## Additional Systems

- Pet system implementation.
- Multiplayer-ready gameplay systems, fully server-authoritative.
- Dedicated server support across all core features.

## Technical Highlights

- Modular, data-driven skill architecture using instanced behaviors.
- Server-based map travel system with database-backed discovery.
- Extensive use of Unreal subsystems (Asset Manager, Significance Manager).
- Strong focus on scalability, performance, and tooling.
- Faithful recreation of legacy MMO mechanics with modern architecture.

## Project Status

This project is an **active remake** with core systems implemented and running in **dedicated multiplayer servers**.

The foundation supports:
- Multiple concurrent maps
- High player counts
- Rapid content iteration
- Custom server configurations
