---
project_name: 'GameJamBmad'
user_name: 'Youssef'
date: '2026-02-04'
sections_completed: ['technology_stack', 'engine_rules', 'performance_rules', 'organization_rules', 'patterns', 'testing_rules', 'platform_rules', 'anti_patterns']
status: 'complete'
rule_count: 32
optimized_for_llm: true
---

# Project Context for AI Agents

_This file contains critical rules and patterns that AI agents must follow when implementing game code in this project. Focus on unobvious details that agents might otherwise miss._

---

## Technology Stack & Versions

**Core Technologies:**
- **Engine:** Godot 4.3+ (Stable Release)
- **Language:** GDScript (Typed)
- **Platform:** PC (Windows)
- **VCS:** Git (Standard .gitignore for Godot)

**Critical Dependencies:**
- **Standard Library:** Uses standard Godot nodes and Singletons
- **Input System:** Godot Input Map (Action-based)
- **Physics:** Godot Physics 2D (CharacterBody2D based)

---

## Critical Implementation Rules

### Engine-Specific Rules (Godot 4.3+)

- **Typing:** STRICT static typing required (`var x: int`, `func foo() -> void`) for performance/safety.
- **Node Access:** Use `%UniqueName` access (Scene Unique Nodes) for scene-internal nodes to prevent path fragility. NEVER use absolute paths.
- **Communication:**
  - **Down (Parent -> Child):** Direct function calls.
  - **Up (Child -> Parent):** Signals only. NEVER `get_parent()`.
  - **Sideways (Sibling -> Sibling):** Via Parent or SignalBus.
- **Lifecycle:**
  - `_ready()`: Child-dependent initialization.
  - `_enter_tree()`: minimal self-initialization only.
- **Resources:** Prefer `Resource` classes over JSON/Dictionaries for static data definition (Dialogues, Stats).

### Performance Rules

- **Frame Budget (16ms):**
  - NO `instantiate()` or `load()` during gameplay hot paths. Use **Object Pooling** (required for projectiles/effects).
  - Physics logic strictly in `_physics_process(delta)`.
  - Visuals/Interpolation strictly in `_process(delta)`.
- **Optimization:**
  - Use `VisibleOnScreenNotifier2D` to disable off-screen entity processing.
  - Minimize localized `new()` calls in loops/process to avoid GC spikes.

### Code Organization Rules

- **Structure:** Feature-Based (Co-location).
  - `game/core/` -> Singletons (`GameContext.gd`)
  - `game/entities/player/` -> Self-contained Player (Scene + Script + Assets)
  - `game/entities/enemies/`
  - `game/levels/`
  - `game/systems/` -> Generic Components (`Hitbox.gd`)
  - `resources/` -> Custom Resources (`.tres`)
- **Naming Conventions:**
  - **Classes/Nodes:** `PascalCase` (`PlayerController`)
  - **Files/Folders:** `snake_case` (`player_controller.gd`) - **CRITICAL** for cross-platform.
  - **Vars/Funcs:** `snake_case` (`take_damage`)
  - **Constants:** `SCREAMING_SNAKE` (`MAX_SPEED`)
  - **Privates:** `_leading_underscore` (`_recalculate_stats`)

### Project Patterns

- **Corruption Propagator (Pattern):**
  - Use `SignalBus.corruption_changed` to update visuals globally.
  - Entities listening to corruption MUST use a `CorruptionListener` component.
- **Player State Machine:**
  - Use Node-based FSM. Player logic resides in State Nodes, not the main script.
- **Visual Duality:**
  - Use `CanvasModulate` for global ambience.
  - Use specific Shader params for glitch effects.

### Testing & Platform Rules

- **Testing Strategy:**
  - **Pragmatic:** No formal unit tests needed for 48h Jam.
  - **Sandbox:** Maintain `_debug/Sandbox.tscn` to test mechanics in isolation.
- **Platform/Build:**
  - **Case Sensitivity:** STRICTLY use `snake_case` (lowercase) for ALL filenames. Windows ignores case, Web/Linux do not -> Crash.
  - **Input:** ALWAYS use InputMap actions (`is_action_pressed`), NEVER hardcoded keys.

### Critical Don't-Miss Rules

- **Physics:** `move_and_slide()` handles delta time internally for velocity. DO NOT multiply `velocity` by delta before calling it.
- **Memory:** Always `queue_free()` destroyed objects. Hiding them causes leaks.
- **UX Safety:** Pause Menu must ALWAYS require a way to Restart/Quit to prevent softlocks.
- **Debugging:** Use `push_error()` for critical failures in Dev, but ensure they don't crash Prod builds.

---

## Usage Guidelines

**For AI Agents:**

- Read this file before implementing any game code
- Follow ALL rules exactly as documented
- When in doubt, prefer the more restrictive option
- Update this file if new patterns emerge

**For Humans:**

- Keep this file lean and focused on agent needs
- Update when technology stack changes
- Review quarterly for outdated rules
- Remove rules that become obvious over time

Last Updated: 2026-02-04
