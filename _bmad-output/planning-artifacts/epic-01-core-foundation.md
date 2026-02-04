# Epic 1: Core Foundation (Heures 0-8)

**Rationale:** Établir une base technique stable et un mouvement satisfaisant avant toute autre chose.
**Gate:** Le mouvement doit se sentir "tight" avant de continuer.

## Stories

### Setup projet Godot + structure dossiers
- **Priority:** P0
- **Estimate:** 30min
- **Criteria:** Projet compile, dossiers organisés selon l'architecture (game/core, game/entities, etc.). Git init fait.

### Controller joueur (Move, Jump, Wall Slide)
- **Priority:** P0
- **Estimate:** 2h
- **Criteria:** Mouvement fluide, pas de bugs de collision. Implémentation via State Machine.

### Coyote Time + Jump Buffer
- **Priority:** P0
- **Estimate:** 30min
- **Criteria:** Timing tolérant pour le saut, testable en jeu.

### Système de collision + Tilemap de test
- **Priority:** P0
- **Estimate:** 1h
- **Criteria:** Collisions précises, pas de clipping. Tilemap basique fonctionnelle.

### Camera follow basique
- **Priority:** P0
- **Estimate:** 30min
- **Criteria:** Suivi fluide du joueur, pas de jitter.

### Système de mort/respawn instantané
- **Priority:** P0
- **Estimate:** 1h
- **Criteria:** Respawn < 0.5s, position correcte au dernier checkpoint.

### Playtest : Le mouvement est-il satisfaisant ?
- **Priority:** P0
- **Estimate:** 30min
- **Criteria:** Feedback équipe positif sur le Game Feel.
