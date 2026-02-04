# Epic 2: Core Mechanics (Heures 8-20)

**Rationale:** Implémenter les mécaniques cœur qui définissent le "Choix" du joueur (Facilité vs Vérité).
**Gate:** La boucle Accept/Refuse doit être claire et fonctionnelle.

## Stories

### Attaque mêlée + hitbox/hurtbox
- **Priority:** P0
- **Estimate:** 1.5h
- **Criteria:** Hitreg précis, knockback sur ennemi.

### Double Saut (unlock conditionnel)
- **Priority:** P0
- **Estimate:** 1h
- **Criteria:** S'active uniquement si l'objet est accepté. Feedback visuel (Ailes).

### Dash (unlock conditionnel)
- **Priority:** P0
- **Estimate:** 1h
- **Criteria:** I-frames, distance fixe. S'active uniquement si débloqué.

### Système de Corruption (variable cachée)
- **Priority:** P0
- **Estimate:** 1h
- **Criteria:** Variable incrémente correctement dans GameContext, persiste entre scènes. Utilise le pattern CorruptionPropagator.

### Glitch de contrôle (input hijack)
- **Priority:** P1
- **Estimate:** 1.5h
- **Criteria:** Se déclenche aléatoirement si corruption élevée. Inverse inputs ou force saut.

### Ennemis basiques (patrouille, volant)
- **Priority:** P1
- **Estimate:** 2h
- **Criteria:** IA prévisible (aller-retour), tuables, blessent le joueur.

### Robot compagnon (follow + dialogue trigger)
- **Priority:** P0
- **Estimate:** 2h
- **Criteria:** Suit le joueur avec lissage, déclenche dialogues via triggers de zone.

### Système de dialogue (bulles de texte)
- **Priority:** P0
- **Estimate:** 1.5h
- **Criteria:** Texte s'affiche au dessus du speaker, input pour avancer. Données chargées depuis Resources.

### Playtest : Le choix Facile/Difficile fonctionne ?
- **Priority:** P0
- **Estimate:** 30min
- **Criteria:** Le joueur comprend le dilemme moral/gameplay.
