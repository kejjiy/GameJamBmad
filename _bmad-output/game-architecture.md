---
title: 'Game Architecture'
project: 'GameJamBmad'
date: '2026-02-04'
author: 'Youssef'
version: '1.0'
stepsCompleted: [1, 2, 3, 4, 5, 6, 7, 8, 9]
status: 'complete'
engine: 'Godot 4.3+'
platform: 'PC (Windows)'

# Source Documents
gdd: 'gdd.md'
epics: null
brief: 'game-brief.md'
---

# Game Architecture

## Executive Summary

**Daiju** architecture is designed for **Godot 4.3+** targeting **PC (Windows)**.

**Key Architectural Decisions:**

- **Engine:** Godot 4.3+ for its lightweight nature, rapid iteration in GDScript, and native 2D support ideal for a 48h Jam.
- **State Management:** Singleton Pattern (`GameContext`, `SignalBus`) for simple, global state access (Corruption, Unlocks) essential for speed; coupled with a **Hierarchical State Machine** for the complex Player Controller logic.
- **Visual Duality:** Hybrid approach using `CanvasModulate` + Global Shaders for widely affecting the game atmosphere (Warm/Cold), with specific sprite swaps for key narrative elements, managed via a novel **Corruption Propagator** pattern.

**Project Structure:** **Feature-Based Co-Location** organization (e.g., `game/entities/player/`) to minimize merge conflicts for a 5-person team, with clear separation of Core logic, Entities, and Assets.

**Implementation Patterns:** **5** patterns defined (Reverse Observer, FSM, Composition, SignalBus, Unique Names) ensuring AI agent consistency and strictly enforced **static typing**.

**Ready for:** Epic implementation phase

---

## Development Environment

### Prerequisites

- **Godot Engine 4.3+** (Standard version, .NET version NOT required as we use GDScript) - [Download](https://godotengine.org/download)
- **Git** - For version control.
- **Visual Studio Code** (Optional but recommended for external editing) with `godot-tools` extension.

### AI Tooling (MCP Servers)

The following MCP servers were selected during architecture to enhance AI-assisted development:

| MCP Server | Purpose | Install Type |
| ---------- | ------- | ------------ |
| **Godot MCP (bradypp)** | Direct scene inspection, node modification, and debug output capture. | Node.js MCP server |

**Setup:**

1.  **Clone the Repo:**
    ```bash
    git clone https://github.com/bradypp/godot-mcp.git
    cd godot-mcp
    ```
2.  **Build:**
    ```bash
    npm install
    npm run build
    ```
3.  **Configure Client:**
    Add the server to your MCP client configuration (e.g., `claude_desktop_config.json`) pointing to the built `index.js`.

These give your AI assistant direct access to **Godot** for scene inspection, asset queries, and context-aware code generation.

### Setup Commands

```bash
# 1. Create Project Directory
mkdir -p game/entities/player
mkdir -p game/entities/enemies
mkdir -p game/entities/companion
mkdir -p game/core
mkdir -p game/levels
mkdir -p game/ui
mkdir -p game/systems
mkdir -p assets/audio
mkdir -p assets/shaders
mkdir -p resources/dialogues

# 2. Initialize Git
git init
echo ".import/" >> .gitignore
echo ".godot/" >> .gitignore
echo "export_presets.cfg" >> .gitignore

# 3. Create Placeholder Scripts (to confirm structure)
touch game/core/GameContext.gd
touch game/core/SignalBus.gd
```

---

## Document Status

This architecture document is being created through the GDS Architecture Workflow.

**Steps Completed:** 9 of 9 (Completion)

---

## Project Context

### Game Overview

**Daiju** - Puzzle-platformer psychologique en 2D pour Game Jam 48h. Une IA malveillante déguisée en compagnon mignon tente de contrôler le joueur via des mécaniques d'assistance (Double Saut, Dash). Dissonance cognitive entre "Facilité/Corruption" et "Difficulté/Vérité".

### Technical Scope

**Platform:** PC (Windows)
**Genre:** Action Platformer (Precision + Puzzle)
**Project Level:** Intermediate (Game Jam Scope)

### Core Systems

| System | Complexity | GDD Reference |
| :--- | :--- | :--- |
| **Player Controller (Dual Mode)** | High | GDD Core Gameplay |
| **Corruption System (Meta-Logic)** | Medium | GDD Progression |
| **Input Hijack (Glitch Mechanic)** | High | GDD Mechanics |
| **Dialogue System (Trigger/State)** | Medium | GDD Art/Audio |
| **World State (Visual Duality)** | High | GDD Art/Audio |

### Technical Requirements

- **Engine:** Godot 4.3+ (2D)
- **Performance:** 60 FPS Stable (Hard constraint for platformer feel)
- **Input:** Zero latency (<16ms), Gamepad + Keyboard support
- **Architecture:** Modular Scene structure to avoid merge conflicts (5 devs)
- **Assets:** Pixel Art + Shaders (Bloom, God Rays, Corruption Overlay)

### Complexity Drivers

**High Complexity:**
*   **Input Hijack / Glitch:** Prendre le contrôle du joueur sans briser la physique ni causer de softlock.
*   **Visual Duality:** Shader global pour basculer entre monde "Mignon" et "Vrai" sans dupliquer tous les assets.

**Novel Concepts:**
*   **"Anti-Power Up":** Les upgrades (Double saut) sont des malus narratifs cachés. Le système doit tracker l'état "Moral" du joueur de manière invisible.

**Technical Risks:**
*   **Softlocks:** Risque élevé avec les glitches de contrôle et les popups de dialogue en plein saut.
*   **Git Merge Conflicts:** 5 personnes sur 48h sur un moteur basé sur des fichiers scènes binaires (.tscn). Architecture stricte requise.

### Technical Risks

1.  **Scope Creep:** 5 niveaux en 48h est très ambitieux. Architecture doit permettre de couper des niveaux facilement.
2.  **Physics Bugs:** Godot 4 `CharacterBody2D` peut avoir des soucis de collision (tunneling) à haute vitesse (Dash).
3.  **State Management:** Synchro entre l'état de corruption et les visuels/dialogues/physique doit être robuste.

---

## Engine & Framework

### Selected Engine

**Godot 4.3+ (Stable Release)**

**Rationale:**
*   **Lightweight & Fast:** Idéal pour une Jam 48h, démarrage instantané, export rapide.
*   **2D Native:** Pixel-perfect natif, contrairement à Unity/Unreal qui sont 3D-first.
*   **Scene System:** Parfait pour l'isolement des tâches (5 devs) via l'instanciation de scènes.
*   **GDScript:** Itération ultra-rapide, typage statique optionnel (que nous forcerons ici pour la propreté).

### Implementation Strategy

**Starter Template:** Custom (From Scratch)
**AI Tooling:** **Godot MCP (bradypp)** - Pour permettre à l'IA d'inspecter et modifier les scènes en temps réel.

### Engine-Provided Architecture

| Component | Solution | Notes |
| :--- | :--- | :--- |
| **Rendering** | Godot 2D (Forward+) | Supporte nativement Lights, Shadows, Shaders 2D. |
| **Physics** | Godot Physics 2D | `CharacterBody2D` pour le joueur, `Area2D` pour les triggers. |
| **Audio** | AudioServer | Bus Layout (Master, SFX, Music, Dialogue). |
| **Input** | InputMap | Abstraction Clavier/Manette native. |
| **Scene Management** | SceneTree | `change_scene_to_file()` pour les niveaux. |
| **UI** | Control Nodes | Système d'ancrage puissant pour le multi-résolution. |

### Remaining Architectural Decisions

Les décisions suivantes doivent être prises explicitement (non fournies par défaut) :

1.  **Shared State Management:** Comment partager l'état "Corruption" entre le Joueur, l'UI et le Monde ? (Singleton vs Resource).
2.  **Save System:** Minimal pour Jam, mais persistance entre scènes requise.
3.  **Asset Loading:** Chargement des niveaux sans freeze (Async loading ?).
4.  **Dialogue System:** Architecture des données (JSON, Resource, CSV ?).

---

## Architectural Decisions

### Decision Summary

| Category | Decision | Version | Rationale |
| :--- | :--- | :--- | :--- |
| **State Management** | **Singleton (Autoload)** | Godot 4.x | Standard Godot pour partage simple de données globales (Corruption, Inventory) en Jam. |
| **Dialogue System** | **Custom Resources** | Godot 4.x | Permet l'édition dans l'inspecteur, typage fort, et découplage code/données. |
| **Visual Duality** | **Hybrid (CanvasModulate)** | Godot 4.x | Compromis coût/qualité optimal : Shader global pour l'ambiance + Sprites spécifiques pour objets clés. |
| **Input Handling** | **Input Map + State Machine** | Godot 4.x | Découplage de la logique d'input (PlayerController) et de l'état (Normal, Hijacked, Cutscene). |

### State Management

**Approach:** Singleton Pattern (`GameContext`, `SignalBus`)

Nous utiliserons deux Singletons principaux :
1.  **GameContext:** Stocke les données pures (`corruption_level`, `unlocked_abilities`).
2.  **SignalBus:** Gère les événements globaux (`on_player_died`, `on_dialogue_started`) pour éviter le couplage direct entre scènes.

### Data Persistence

**Save System:** `ConfigFile` (Format style INI/CFG)

Simple et suffisant pour sauvegarder :
- Dernier Checkpoint (Nom de scène + Position)
- État de Corruption et unlocks
- Settings (Volume)

### Visual System (Duality)

**Strategy:** Global Shader & Modulate

- **CanvasModulate:** Un nœud global teinte tout le niveau (Chaud -> Froid).
- **WorldEnvironment:** Change le Glow/Bloom selon la corruption.
- **Glitch Overlay:** Un `ColorRect` avec shader en top-layer pour les effets de corruption d'écran.

### Architecture Decision Records

**ADR-01: Resource-Based Dialogues**
*   **Contexte:** Besoin d'itérer vite sur les textes sans recompil/code.
*   **Décision:** Utiliser `Resource` (`DialogueData.gd`) plutôt que JSON.
*   **Conséquence:** Les designers peuvent créer des fichiers `.tres` directement dans le FileSystem et les drag-and-drop sur les triggers.

**ADR-02: Finite State Machine (FSM) pour le Player**
*   **Contexte:** Le joueur a des états complexes (Normal, WallSlide, Dash, Hijacked, Dead).
*   **Décision:** Implémenter une FSM stricte (`PlayerState` nodes).
*   **Conséquence:** Code plus verbeux mais ZERO possibilité d'avoir "Dash + WallSlide" en même temps (bug fréquent).

---

## Cross-cutting Concerns

These patterns apply to ALL systems and must be followed by every implementation.

### Error Handling

**Strategy:** Fail Safe but Loud (in Dev) / Silent (in Prod)

**Error Levels:**
- **CRITICAL:** Game state impossible (e.g., Level scene missing). -> `push_error()` + Return to Main Menu.
- **ERROR:** Feature broken but playable (e.g., SFX missing). -> `push_warning()` + Continue without sound.
- **INFO:** Game milestones (e.g., Level started). -> `print()`.

**Example:**

```gdscript
func load_level(path: String) -> void:
    if not ResourceLoader.exists(path):
        push_error("CRITICAL: Level not found at " + path)
        return # Fail safe, don't crash
    
    var scene = load(path)
    # ...
```

### Logging

**Format:** `[CATEGORY] Message`
**Destination:** Godot Console / `user://logs/latest.log` (Optional)

**Log Levels:**
- `[AUDIO]`
- `[GAMEPLAY]`
- `[SYSTEM]`
- `[AI]`

**Example:**

```gdscript
print("[AUDIO] Playing sound: ", sound_name)
```

### Configuration

**Approach:** `GameConfig` Singleton

**Configuration Structure:**
- **Constants:** `MAX_HP`, `GRAVITY` (Hardcoded `const` in scripts for easy optimization).
- **Settings:** `MasterVolume`, `Fullscreen` (Saved in `user://settings.cfg`).
- **Balancing:** Export variables on Nodes (`@export var jump_force: float`) for Level Design tweaking.

### Event System

**Pattern:** Global SignalBus (Observer)

**Event Naming:** `verb_noun` (past tense preferred) -> `player_died`, `level_completed`, `item_collected`.

**Example:**

```gdscript
# SignalBus.gd
signal player_died()

# Player.gd
func die():
    SignalBus.player_died.emit()

# HUD.gd
func _ready():
    SignalBus.player_died.connect(_on_player_died)
```

### Debug Tools

**Available Tools:**
- **Cheat Menu (F12):** Invisible UI to Teleport/Unlock All/Reset Save.
- **Visual Debug:** Draw Hitboxes/Patrol Paths (Toggle via Cheat Menu).
- **Log Viewer:** In-game console for builds (optional).

**Activation:** Input Action `debug_toggle` (F12), stripping in Release builds via `#if DEBUG` preprocessor mimics.

---

## Project Structure

### Organization Pattern

**Pattern:** Feature-Based Co-Location

**Rationale:** Keeps all related resources (scripts, scenes, sprites) in one folder, making it easier for a team of 5 to work on separate features without conflicts.

### Directory Structure

```
res://
├── .godot/                 # Engine cache (Gitignored)
├── _debug/                 # Sandbox and test scenes (Gitignored in Release)
│   └── Sandbox.tscn
├── assets/                 # Shared RAW assets only
│   ├── audio/
│   │   ├── music/
│   │   └── sfx/
│   ├── fonts/
│   └── shaders/            # Global shaders
├── game/                   # GAME LOGIC
│   ├── core/               # Singletons and Autos
│   │   ├── GameContext.gd
│   │   ├── SignalBus.gd
│   │   └── GameConfig.gd
│   ├── entities/           # Everything that moves
│   │   ├── player/         # Self-contained Player
│   │   │   ├── Player.tscn
│   │   │   ├── Player.gd
│   │   │   ├── states/
│   │   │   └── assets/
│   │   ├── enemies/
│   │   │   ├── crawler/
│   │   │   └── flyer/
│   │   └── companion/      # The Robot
│   ├── levels/             # Level Scenes
│   │   ├── Level01.tscn
│   │   └── Level02.tscn
│   ├── systems/            # Components
│   │   ├── Hitbox.gd
│   │   ├── Hurtbox.gd
│   │   └── DialogueTrigger.gd
│   └── ui/
│       ├── HUD.tscn
│       └── Menus/
├── resources/              # Custom Data Resource Instances
│   ├── dialogues/
│   └── items/
└── export/                 # Export presets
```

### System Location Mapping

| System | Location | Responsibility |
| :--- | :--- | :--- |
| **Player Controller** | `game/entities/player/` | Input handling, movement FSM. |
| **Game Manager** | `game/core/GameContext.gd` | Global state, corruption level. |
| **Dialogue Data** | `resources/dialogues/` | Text content (Resource files). |
| **Audio** | `assets/audio/` | Raw WAV/OGG files. |
| **UI Logic** | `game/ui/` | Scripts controlling menus. |
| **Shaders** | `assets/shaders/` | Visual effects code (`.gdshader`). |

### Naming Conventions

#### Files
- **Scripts:** `snake_case.gd` (e.g., `player_controller.gd`)
- **Scenes:** `PascalCase.tscn` (e.g., `Player.tscn`)
- **Assets:** `snake_case` (e.g., `player_jump.png`)

#### Code Elements
| Element | Convention | Example |
| :--- | :--- | :--- |
| **Classes** | `PascalCase` | `class_name PlayerEntity` |
| **Nodes** | `PascalCase` | `$PlayerBody`, `%HealthBar` |
| **Vars** | `snake_case` | `var movement_speed: float` |
| **Signals** | `snake_case` | `signal health_changed` |
| **Consts** | `SCREAMING_SNAKE` | `const MAX_SPEED = 300` |

#### Architectural Boundaries

1.  **Strict File Casing:** All file paths MUST be lowercase/snake_case for cross-platform compatibility.
2.  **No Cyclic Dependencies:** `game/core` cannot reference `game/entities`. Entities must use Signals to talk up to Core.

---

## Implementation Patterns

### Novel Patterns

#### Corruption Propagator (Reverse Observer)

**Purpose:** Allows global "Corruption" state to affect scattered entities (UI, Shaders, Physics) without tight coupling.

**Components:**
- `GameContext` (Singleton): Holds `corruption_level`.
- `CorruptionListener` (Component): Attached to entities (Enemies, Props).
- `SignalBus`: Transmits `corruption_changed` event.

**Data Flow:**
1. Player accepts Item -> Calls `GameContext.add_corruption(1)`.
2. `GameContext` emits `SignalBus.corruption_changed(new_level)`.
3. All `CorruptionListener` nodes receive signal -> Trigger visual change (Sprite Swap / Shader Param).

**Implementation Guide:**
```gdscript
# corruption_listener.gd
extends Node
class_name CorruptionListener

@export var threshold: int = 3
@export var corrupted_texture: Texture2D

func _ready():
    SignalBus.corruption_changed.connect(_on_corruption_changed)

func _on_corruption_changed(level: int):
    if level >= threshold:
        get_parent().texture = corrupted_texture
```

### State Patterns

**Pattern:** Hierarchical State Machine (Node-Based)

**Example:**
```gdscript
# player_state_machine.gd
func _physics_process(delta):
    if current_state:
        current_state.update(delta)

# state_idle.gd
func update(_delta):
    if player.velocity.x != 0:
        transition_to("Run")
    if Input.is_action_just_pressed("jump"):
        transition_to("Jump")
```

### Entity Patterns

**Creation:** Composition over Inheritance

**Example:**
Instead of `class Crawler extends Enemy`, use:
```tscn
Crawler (CharacterBody2D)
├── HealthComponent (Node)
├── HitboxComponent (Area2D)
└── PatrolBehavior (Node)
```

### Communication Patterns

**Pattern:** Signal Bus (Many-to-Many)

**Example:**
```gdscript
# Use for distant systems
SignalBus.dialogue_started.emit(dialogue_resource)
```

### Data Patterns

**Access:** `%SceneUniqueNames`

**Example:**
```gdscript
# GOOD (Robust)
@onready var sprite = %Sprite2D

# BAD (Fragile)
@onready var sprite = get_node("Visuals/Body/Sprite2D")
```

### Consistency Rules

| Pattern | Convention | Enforcement |
| :--- | :--- | :--- |
| **Typing** | Strict Static Typing | `func foo(x: int) -> void:` (Parser Error if missing) |
| **Node Access** | Unique Names | Use `%` for internal scene nodes. |
| **Updates** | Process Separation | `_physics_process` for bodies, `_process` for visuals. |

---

## Architecture Validation

### Validation Summary

| Check | Result | Notes |
| :--- | :--- | :--- |
| Decision Compatibility | Pass | Engine + Patterns aligned (Godot/Singleton/Signals). |
| GDD Coverage | Pass | All core systems (Corruption, Duality, Player) architected. |
| Pattern Completeness | Pass | Creation, Communication, State, and Data patterns defined. |
| Epic Mapping | Pass | All Epics map to specific architectural components. |
| Document Completeness | Pass | No placeholders, all sections complete. |

### Coverage Report

**Systems Covered:** 100%
**Patterns Defined:** 5 (Reverse Observer, HSM, Composition, SignalBus, UniqueNames)
**Decisions Made:** 10+ (Engine, Structure, State, etc.)

### Issues Resolved

- Confirmed Engine Selection (Godot 4.3+).
- Defined "Corruption Propagator" novel pattern.
- Established strict naming conventions for cross-platform safety.

### Validation Date

2026-02-04
