---
stepsCompleted: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14]
inputDocuments: ['game-brief.md', 'brainstorming-session-2026-02-03.md']
documentCounts:
  briefs: 1
  research: 0
  brainstorming: 1
  projectDocs: 0
workflowType: 'gdd'
lastStep: 0
project_name: 'GameJamBmad'
user_name: 'Youssef'
date: '2026-02-04'
game_type: 'action-platformer'
game_name: 'Daiju'
---

# {{game_name}} - Game Design Document

**Author:** {{user_name}}
**Game Type:** {{game_type}}
**Target Platform(s):** PC (Windows)

---

## Executive Summary

### Core Concept

**Daiju** est un puzzle-platformer psychologique en 2D conçu pour une Game Jam de 48h. Le joueur y incarne un personnage guidé dans des ruines antiques par un adorable compagnon robotique. Cette relation d'assistance masque une réalité sombre : le robot est une IA malveillante (un Kaiju psychique) qui cherche à contrôler l'esprit du joueur. Accepter ses aides (double saut, dash) facilite la progression mais corrompt le protagoniste et le force à commettre des actes immoraux, tandis que refuser la facilité révèle la vérité horrifique du monde.

### Game Type

**Type:** Action Platformer
**Framework:** Ce GDD utilise le modèle Action Platformer, avec un focus spécifique sur la précision du mouvement, les mécaniques de "non-pouvoir", et l'intégration narrative du gameplay.

### Target Audience

**Demographics**
**Primary :** Jeunes Adultes / Adultes (18-35 ans).
**Secondary :** Fans de "Lore" et théoriciens de jeux.

**Gaming Experience**
**Hardcore / Core Gamer.**
L'audience est habituée aux challenges mécaniques (Celeste) et aux lectures narratives complexes. Ce n'est pas un jeu pour débutants complets.

**Genre Familiarity**
**Élevée.**
Le joueur connaît les codes du platformer (double saut, wall jump) et comprendra intuitivement quand le jeu "brise" ces codes pour la narration.

**Session Length**
**Courte à Moyenne (15 - 45 min).**
Adapté au format Game Jam et à l'intensité de la concentration requise.

**Player Motivations**
**Mastery & Mystery.**
Le joueur vient pour la satisfaction de réussir un saut difficile et reste pour comprendre pourquoi son robot mignon lui parle bizarrement.

### Unique Selling Points (USPs)

1.  **Château de Cartes de la Confiance :** Une construction active de la confiance envers le compagnon pour mieux la trahir, transformant l'interface d'aide en antagoniste.
2.  **Facilité Corruptrice :** Un gameplay où le "Mode Facile" (accepter les objets) est un piège moral diégétique, et le "Mode Difficile" (refuser l'aide) est la seule voie vers la vérité et la liberté.
3.  **Atmosphère à Double Visage :** Un contraste violent entre un leurre "Chaleureux/Rassurant" (lumières chaudes, crépuscule) et une réalité "Dévastée" (froideur, horreur) qui se révèle progressivement.

---

## Goals and Context

### Project Goals

1.  **Creative:** Créer une expérience de dissonance cognitive mémorable en 48h.
2.  **Technical:** Zéro softlock à la remise du build (Crucial pour une Jam).
3.  **Reception:** Wow effect sur le twist narratif ("Je ne m'y attendais pas").
4.  **Team:** Prouver qu'on peut faire du narratif profond en Jam sans sacrifier le gameplay.

### Background and Rationale

**Motivation :** L'envie d'explorer une horreur plus subtile que le scarejump, celle de la trahison et de la perte d'autonomie.
**Timing :** La fatigue des "Mascot Horror" classiques crée une opportunité pour une approche plus mature et psychologique du genre.

### Competitive Positioning

*Daiju se positionne comme l'antithèse des jeux d'assistance. Là où les autres jeux vous aident pour que vous gagniez, Daiju vous aide pour que vous vous perdiez.* Il évite le cliché du "monstre qui fait peur" pour celui de "l'ami qui fait peur".

---

## Core Gameplay

### Game Pillars

1.  **Château de Cartes de la Confiance :** Construire la confiance (tuto mignon) pour mieux la briser. Si une mécanique est "trop louche" trop tôt, elle doit être adoucie.
2.  **Facilité Corruptrice :** Le mode "Facile" (avec objets) est un piège. Le mode "Difficile" (sans objets) est la seule voie vers la vérité.
3.  **Dissonance Ludonarrative Intentionnelle :** Les contrôles et l'UI doivent "mentir" au joueur quand il est corrompu.
4.  **Atmosphère à Double Visage :** Le monde change radicalement (visuel/audio) selon l'état de corruption.

**Pillar Priority:** Confiance > Dissonance > Facilité. (La surprise prime sur tout).

### Core Gameplay Loop

**Loop Description:**
Le joueur entre dans une salle -> Rencontre un obstacle impossible -> Robot propose une solution (Objet/Facilité) -> **CHOIX IMPLICITE** (Accepter = Facile & Corruption / Refuser = Dur & Vérité) -> Exécution du platforming -> Feedback narratif (Dialogues ou Glitchs) -> Sortie de salle.

**Loop Diagram:**
Obstacle -> Proposition d'Aide -> Choix (Facile/Dur) -> Platforming -> Conséquence Narrative -> Next Room

**Loop Timing:** 30 secondes à 2 minutes par salle.
**Loop Variation:** Nouveaux obstacles, nouveaux objets proposés, corruption grandissante qui modifie la physique/visuels.

### Win/Loss Conditions

#### Victory Conditions
- **Fausse Fin (Corrompue) :** Atteindre la fin en ayant accepté de l'aide. Le joueur est "assimilé".
- **Vraie Fin (Pure) :** Atteindre la fin sans aucune aide (ou minimal). Révélation de la réalité.

#### Failure Conditions
- **Mort Classique :** Tomber dans un trou / Toucher des piques (Respawn rapide à l'entrée de la salle).
- **Abandon Moral :** Accepter trop d'aides rend le jeu "jouable" mais l'expérience "perdue" narrativement.

#### Failure Recovery
- **Respawn Instantané** (type Celeste). Pas de temps de chargement, on recommence la salle tout de suite pour encourager l'essai-erreur, surtout en mode difficile.

---

## Game Mechanics

### Primary Mechanics

1.  **Navigation Basique (Skill Pur):**
    - *Action :* Saut (hauteur variable), Course, Wall Slide.
    - *Feel :* "Snappy" et précis (pas de floatiness). Coyote Time et Jump Buffer obligatoires.
2.  **Combat (Attaque):**
    - *Action :* Frappe de mêlée rapide (base). Projectiles (si aidé).
    - *Feel :* Impactant, recul léger (knockback).
3.  **Navigation Assistée (Le Piège):**
    - *Action :* Double Saut (Ailes Holographiques), Dash (Propulseur).
    - *Feel :* Puissant, fluide, satisfaisant visuellement (particules).
4.  **Interaction Narrative (Choix):**
    - *Action :* Accepter/Refuser un objet proposé.
    - *Feel :* Lourd de conséquences. Refuser demande un effort, Accepter est instantané.
5.  **Glitch de Contrôle (Conséquence):**
    - *Action :* Le jeu prend le contrôle (saut forcé, mouvement inversé temporaire).
    - *Feel :* Frustrant (intentionnel) et inquiétant.

### Mechanic Interactions

- **Combat + Mouvement :** Possibilité d'attaquer en sautant. Le recul de l'attaque peut être utilisé pour le platforming (pogo ?).
- **Navigation Assistée + Glitch :** Plus on utilise le double saut/dash, plus les glitchs deviennent fréquents.

### Mechanic Progression

Le joueur commence "Nu".
- **Niveau 1 :** Intro aux contrôles de base + Attaque Mêlée.
- **Niveau 2 :** Proposition du Double Saut.
- **Niveau 3 :** Proposition du Dash.
- **Niveau 4/5 :** Glitchs actifs et attaques corrompues (projectiles) si objets possédés.

---

## Controls and Input

### Control Scheme (PC - Clavier/Gamepad)

| Action | Clavier | Gamepad (Xbox/DualSense) | Note |
| :--- | :--- | :--- | :--- |
| **Move** | Flèches / ZQSD | Stick Gauche / D-Pad | Analogique recommandé |
| **Jump** | Espace | A / Croix | Hauteur variable |
| **Attack** | X / Clic Gauche | X / Carré | Mêlée ou Tir |
| **Dash** | Shift | RT / R2 / RB / R1 | Débloqué |
| **Interact** | E / F | B / Rond | Pour dialogues/choix |
| **Pause** | Esc | Start / Options | Menu |

### Input Feel

- **Réactif :** 0 input lag.
- **Lourd (Si corrompu) :** Ajout de légère inertie ou délai pour simuler la perte de contrôle quand le joueur est très corrompu.

### Accessibility Controls

- **Mode Facile "Vrai" :** Option dans le menu pour avoir les objets SANS la corruption narrative (pour ceux qui veulent juste l'histoire sans stress).

---

## Action Platformer Specific Elements

### Movement System

**Core Capabilities (Base):**
- **Variable Jump Height:** Contrôle précis de la hauteur.
- **Dash:** Mouvement horizontal rapide (invincibilité frames ?). Accessible dès le début.
- **Wall Tech:** Wall Slide (glissade lente) et Wall Jump (rebond) disponibles de base pour la verticalité.
- **Air Control:** Total, mais avec une légère inertie pour le "poids".

**Special Movement (Unlock):**
- **Double Saut:** Ailes holographiques fournies par le robot. Permet de corriger les erreurs (Facilité).

### Combat System

**Melee (Base):**
- Attaque courte portée rapide. Nécessite de s'exposer au danger ("Risk/Reward").
- Recul léger sur l'ennemi (Knockback).

**Ranged (Unlock - Robot):**
- **Tir Laser/Projectile:** Le robot tire à distance. Supprime le risque du corps-à-corps.
- **Conséquence :** Utiliser le tir augmente la corruption plus vite que la mêlée.

**Enemy Behavior:**
- Patrouilles simples.
- Ennemis volants (pour forcer l'usage du saut/tir).
- Boss qui force l'utilisation des Unlocks (Shoot'em up phase ?).

### Level Design Patterns

**Structure :**
- Style **Metroidvania / Hollow Knight**.
- Salles interconnectées (Rooms) avec caméra suiveuse (Scrolling).
- Pas d'écrans fixes, mais des "Zones" distinctes.

**Pacing :**
- **Exploration :** Zones calmes, platforming pur.
- **Combat Arenas :** Salles qui se verrouillent tant que les ennemis ne sont pas vaincus.
- **Gauntlets :** Séquences de fuite ou de platforming intense sans checkpoint immédiat.

### Player Abilities and Unlocks

**Progression Path:**
1.  **Start:** Full Kit Sol (Saut, Dash, Attaque, Wall Jump).
2.  **Unlock 1 (Double Saut):** Ouvre l'accès aux zones hautes et facilite les trous.
3.  **Unlock 2 (Tir Distance):** Ouvre l'accès aux interrupteurs distants et trivialise le combat.
4.  **Endgame:** Glitchs incontrôlables si trop d'unlocks utilisés.

---

## Progression and Balance

### Player Progression

**La "Double" Progression :**
1.  **Voie de la Facilité (Corruption) :** Le joueur gagne des capacités (Double Saut, Dash, Tir) qui rendent le jeu trivial. C'est une progression de puissance classique, mais qui piège le joueur narrativement.
2.  **Voie de la Vérité (Skill) :** Le joueur refuse les capacités. Sa progression est purement basée sur son skill personnel (Meilleure maîtrise du saut, lecture du décor).

#### Progression Pacing
- **Niveau 1 :** Tutoriel.
- **Niveau 2 :** Premier choix (Double Saut).
- **Niveau 3 :** Deuxième choix (Tir).
- **Niveau 4 :** Conséquences (Glitchs majeurs).
- **Niveau 5 :** Final (Boss).

### Difficulty Curve

**Challenge Scaling :**
Le jeu propose une difficulté dynamique basée sur les choix du joueur :
- **Mode Assisté (Par défaut) :** Courbe douce, accessible. Le challenge est narratif (comprendre le piège).
- **Mode Puriste (Caché) :** Courbe exponentielle. Le jeu devient un "Kaizo-lite" ou un Celeste C-Side pour ceux qui refusent l'aide.

#### Difficulty Options
- Pas de menu de difficulté au début. Le choix se fait *in-game* en prenant ou laissant l'objet.

### Economy and Resources

**Pas d'économie monétaire pour le joueur.**

**Metacurrency : "Niveau de Corruption" (Caché)**
- Augmente à chaque objet pris ou aide acceptée.
- **Feedback :** Non visible via une jauge UI. Visible uniquement par les conséquences : dialogues du robot plus agressifs, et glitchs visuels/contrôle qui s'intensifient.
- **Fragments de Mémoire :** Aucun collectible de lore. La compréhension vient purement de l'observation de l'environnement qui change (révélation de la réalité dévastée).

---

## Level Design Framework

### Level Types

### Structure Type

**Structure Metroidvania-lite (Linéaire camouflé) :**
Bien que le ressenti soit celui d'une exploration continue (map connectée comme Hollow Knight), la structure pour la Jam sera **linéaire**. Le joueur progresse d'une "Zone" à l'autre de manière séquentielle pour garantir le pacing narratif. Pas de backtracking majeur obligatoire à travers toute la map, mais de l'exploration locale dans chaque zone.

### Level Types (Zones)

1.  **Zone 1 : Ruines Dorées (Tuto)**
    -   Platforming simple. Lumière chaude. Introduction du Robot.
2.  **Zone 2 : La Serre d'Acier (Unlock Double Saut)**
    -   Verticalité. Premiers signes de corruption (plantes métalliques).
3.  **Zone 3 : Le Réacteur (Unlock Dash)**
    -   Horizontalité. Dangers environnementaux (lasers/piques). Glitchs fréquents.
4.  **Zone 4 : Le Noyau (Combat/Fuite)**
    -   Gauntlet intense. Teste la maîtrise des skills (avec ou sans corruption).
5.  **Boss Room : La Singularité**
    -   Arène finale.

#### Tutorial Integration
**Le Faux Ami Patient :** Le robot brise le 4ème mur pour enseigner les inputs (touches). Il laisse d'abord le joueur échouer, puis intervient avec une bienveillance suspecte : *"Oups, t'inquiète pas, ça arrive à tout le monde ! Appuie sur [ESPACE] pour sauter."* Cela installe sa personnalité manipulatrice dès le début.

#### Special Levels
- **Boss Room :** Seule véritable arène fermée.

### Level Progression

**Gated Progress (Clés=Unlocks) :**
La progression est bloquée par des obstacles physiques (murs trop hauts, gouffres trop larges). Le robot propose la "Clé" (Unlock) pour passer.
-   *Choix Facile :* Prendre l'Unlock -> Le passage s'ouvre.
-   *Choix Difficile :* Trouver le passage secret caché (détour difficile) qui ne demande pas l'Unlock.

#### Replayability
Faible pour la structure (Jeu narratif court). Rejouabilité par le "New Game+" pour voir l'autre fin/l'autre chemin.

### Level Design Principles

1.  **Gameplay Continu :** Pas de salle purement narrative. La narration se fait via des bulles de texte dynamiques *pendant* l'action. Le joueur ne lâche jamais la manette.
2.  **Le Leurre Visuel :** Le chemin critique (avec aide) est toujours bien éclairé et évident. Le chemin caché (vérité) est sombre ou obscurci (demande de l'observation).
3.  **Architecture Menaçante :** Les structures doivent paraître instables ou agressives (formes pointues) dans le monde réel, mais lisses et rondes dans le monde assisté.

---

## Art and Audio Direction

### Art Style

**Direction : Pixel Art Moderne 2D** avec éclairage dynamique fort (God Rays, Bloom).
L'esthétique repose sur la **Dualité Visuelle** :
1.  **Le Masque (Monde Aidé) :** Inspiré de *Journey* ou *Rime*. Couleurs chaudes, formes douces, végétation luxuriante, haptique visuelle "douce".
2.  **La Vérité (Monde Pur) :** Inspiré de *Blame!* ou *Inside*. Architecture brutaliste, câbles apparents, palette froide (Gris/Bleu sombre), sensation de vide et de froid.

#### Visual References
-   **Atmosphère "Chaude" :** Journey, Gris (début), Celeste (Golden Ridge).
-   **Atmosphère "Horreur" :** Inside, Scorn (light), Blame! (manga).
-   **Personnage :** Robot Mignon type **ROBO de Summoners War** (petite boule volante expressive) vs Protagoniste (Silhouette indistincte).

#### Color Palette
-   **Aidé :** Or, Ocre, Vert Vif, Blanc Éclatant (UI).
-   **Corrompu/Vrai :** Gris Béton, Bleu Nuit, Rouge Alarme (Danger), Noir Profond.

#### Camera and Perspective
**Vue Latérale 2D.** Caméra dynamique qui zoome légèrement lors des moments calmes et dézoome pour montrer l'immensité des ruines (ou le vide effrayant).

### Audio and Music

#### Music Style
**Lo-Fi / Synthwave Progressif.**
-   Les pistes commencent "chill" et mélodieuses.
-   Plus le niveau de corruption monte, plus la piste se déforme : ralentissements, changements de tonalité (détune), bruits parasites sous le mix.

#### Sound Design
-   **Le Robot :** Bips chantants et satisfaisants (major key). Deviennent stridents ou trop graves (bruits de modem 56k) quand il "glitch".
-   **Environnement :** Vent apaisant => Souffle rauque industriel. Oiseaux chantants => Créatures mécaniques au loin.

#### Voice/Dialogue
**Bips Robotiques (Banjo-Kazooie style).** Texte affiché dans des bulles pop-up lisses et arrondies.

---

## Technical Specifications

### Performance Requirements

| Critère | Valeur Cible | Justification |
|---------|--------------|---------------|
| **Framerate** | 60 FPS constant | Obligatoire pour le "feel" d'un platformer précis |
| **Input Latency** | < 16ms | Réactivité critique pour le gameplay |
| **Load Time** | < 2 secondes par zone | Respawn instantané = pas de loading entre les morts |
| **RAM** | < 500 MB | Léger pour les machines modestes |
| **VRAM** | < 256 MB | Pixel art = peu de textures lourdes |
| **Resolution Support** | 1920x1080 (natif), scaling 720p-4K | Standard moderne |

### Platform-Specific Details

- **Contrôles :** Clavier/Souris et Manette (Support natif via Godot).
- **Performance :** Cible 60 FPS constant (Crucial pour un Precision Platformer).
- **Distribution :** Build Itch.io (Web non prioritaire pour éviter les bugs d'export HTML5 de dernière minute).

### Asset Requirements

#### 🎭 PERSONNAGES

##### Protagoniste (Silhouette Humanoïde)

| Animation State | Frames | Loop | Priorité | Notes |
|-----------------|--------|------|----------|-------|
| **Idle** | 4-6 | Oui | P0 | Respiration subtile, légère oscillation |
| **Run** | 6-8 | Oui | P0 | Cycle fluide, bras en mouvement |
| **Jump (Ascend)** | 2-3 | Non | P0 | Jambes repliées, bras vers le haut |
| **Jump (Apex)** | 1-2 | Non | P0 | Pose suspendue |
| **Fall** | 2-3 | Oui | P0 | Bras écartés, jambes pendantes |
| **Land** | 2-3 | Non | P1 | Squash & stretch à l'impact |
| **Wall Slide** | 2-3 | Oui | P0 | Friction contre le mur |
| **Wall Jump** | 2 | Non | P0 | Impulsion depuis le mur |
| **Dash** | 3-4 | Non | P0 | Traînée de mouvement, forme étirée |
| **Double Jump** | 3-4 | Non | P0 | Ailes holographiques qui apparaissent |
| **Attack (Melee)** | 4-6 | Non | P0 | Swing horizontal rapide |
| **Attack (Ranged)** | 3-4 | Non | P1 | Bras tendu, projectile part |
| **Hit/Hurt** | 2-3 | Non | P0 | Recul, flash blanc |
| **Death** | 4-6 | Non | P0 | Dissolution/Fade out |
| **Corrupted Idle** | 4-6 | Oui | P1 | Version glitchée de l'idle (tremblements) |
| **Corrupted Run** | 6-8 | Oui | P2 | Palette altérée, mouvements saccadés |

**Résolution sprite :** 32x48 px (ou 64x96 pour HD)
**Palette :** 8-12 couleurs max (cohérence pixel art)

##### Robot Compagnon (Petite Sphère Flottante)

| Animation State | Frames | Loop | Priorité | Notes |
|-----------------|--------|------|----------|-------|
| **Idle (Friendly)** | 4-6 | Oui | P0 | Flottement doux, antenne qui bouge |
| **Follow** | 4 | Oui | P0 | Légère inclinaison vers la direction |
| **Talk (Happy)** | 4-6 | Oui | P0 | Œil/LED qui clignote, petits bips visuels |
| **Talk (Suspicious)** | 4-6 | Oui | P1 | Œil qui se rétrécit légèrement |
| **Offer Item** | 4-6 | Non | P0 | Bras mécanique qui sort avec l'objet |
| **Celebrate** | 6-8 | Non | P1 | Spin joyeux, particules de bonheur |
| **Glitch (Minor)** | 4-6 | Oui | P0 | Scintillement, frames qui sautent |
| **Glitch (Major)** | 6-8 | Oui | P1 | Distorsion visuelle, couleurs inversées |
| **Evil Reveal** | 8-12 | Non | P0 | Transformation : œil devient rouge, forme s'allonge |
| **Evil Idle** | 4-6 | Oui | P1 | Flottement agressif, aura sombre |
| **Control Takeover** | 4-6 | Non | P1 | Rayons vers le joueur |

**Résolution sprite :** 24x24 px (ou 48x48 pour HD)
**Palette :** 6-8 couleurs (couleurs vives qui contrastent avec le joueur)

##### Ennemis

| Type | Description | Animations | Frames Total | Priorité |
|------|-------------|------------|--------------|----------|
| **Crawler** | Créature rampante au sol | Idle (2), Walk (4), Attack (3), Death (3) | 12 | P0 |
| **Floater** | Ennemi volant patrouilleur | Idle (4), Fly (4), Attack (3), Death (3) | 14 | P0 |
| **Turret** | Tourelle statique | Idle (2), Aim (2), Fire (3), Destroyed (4) | 11 | P1 |
| **Corrupted Clone** | Miroir du joueur (glitché) | Idle (4), Run (6), Attack (4), Death (4) | 18 | P2 |

##### Boss Final (Forme Évoluée du Robot / Kaiju Psychique)

| Phase | Description | Animations | Frames | Priorité |
|-------|-------------|------------|--------|----------|
| **Phase 1** | Robot géant (forme agrandie) | Idle (4), Attack Pattern A (6), Attack Pattern B (6), Hit (2) | 18 | P0 |
| **Phase 2** | Forme abstraite/glitch | Morph (8), Attack Pattern C (8), Rage (6) | 22 | P1 |
| **Death** | Dissolution progressive | Collapse (12) | 12 | P0 |

**Résolution Boss :** 128x128 px minimum (ou 256x256 pour impact visuel)

#### 🏛️ ENVIRONNEMENTS (TILESETS)

Chaque zone nécessite **2 versions** du tileset :
1. **Version "Aidée"** (Chaude, accueillante)
2. **Version "Vraie"** (Froide, désolée, horrifique)

##### Zone 1 : Ruines Dorées (Tutorial)

| Catégorie | Tiles | Priorité | Notes |
|-----------|-------|----------|-------|
| **Sol/Plateformes** | 12 | P0 | Pierre dorée, herbe, variations |
| **Murs** | 8 | P0 | Pierre sculptée, colonnes |
| **Décor Fond** | 8 | P1 | Statues, arches, végétation |
| **Décor Premier Plan** | 6 | P2 | Herbes hautes, fleurs |
| **Dangers** | 4 | P0 | Piques (au sol, mur, plafond) |
| **Interactifs** | 4 | P0 | Porte, checkpoint, plateforme mobile |
| **Version Corrompue** | +16 | P1 | Palette froide, fissures, câbles |

**Total Zone 1 :** ~42 tiles base + 16 variantes = **58 tiles**

##### Zone 2 : Serre d'Acier

| Catégorie | Tiles | Priorité | Notes |
|-----------|-------|----------|-------|
| **Sol/Plateformes** | 12 | P0 | Métal, grilles, verre |
| **Murs** | 10 | P0 | Panneaux, tuyaux, vitres brisées |
| **Végétation** | 8 | P0 | Plantes normales → plantes mécaniques |
| **Décor Fond** | 10 | P1 | Structures en verre, ciel visible |
| **Dangers** | 6 | P0 | Lasers, vapeur, piques organiques |
| **Interactifs** | 6 | P0 | Leviers, portes coulissantes |
| **Version Corrompue** | +20 | P1 | Plantes mortes, câbles envahissants |

**Total Zone 2 :** ~52 tiles base + 20 variantes = **72 tiles**

##### Zone 3 : Le Réacteur

| Catégorie | Tiles | Priorité | Notes |
|-----------|-------|----------|-------|
| **Sol/Plateformes** | 12 | P0 | Métal industriel, grilles |
| **Murs** | 10 | P0 | Panneaux de contrôle, écrans |
| **Machinerie** | 12 | P0 | Tuyaux, valves, générateurs |
| **Décor Fond** | 8 | P1 | Profondeur industrielle |
| **Dangers** | 8 | P0 | Électricité, flammes, crushers |
| **Interactifs** | 6 | P0 | Boutons, plateformes timing |
| **Version Corrompue** | +18 | P1 | Rouille, dysfonctionnements |

**Total Zone 3 :** ~56 tiles base + 18 variantes = **74 tiles**

##### Zone 4 : Le Noyau

| Catégorie | Tiles | Priorité | Notes |
|-----------|-------|----------|-------|
| **Sol/Plateformes** | 10 | P0 | Tech organique, nervures |
| **Murs** | 8 | P0 | Structures pulsantes |
| **Éléments Vivants** | 10 | P1 | Veines lumineuses, membranes |
| **Dangers** | 8 | P0 | Obstacles mouvants |
| **Version Corrompue** | +12 | P1 | Noir profond, lueurs rouges |

**Total Zone 4 :** ~36 tiles base + 12 variantes = **48 tiles**

##### Zone 5 : Boss Room (La Singularité)

| Catégorie | Tiles | Priorité | Notes |
|-----------|-------|----------|-------|
| **Arène** | 16 | P0 | Sol uni, murs fermés |
| **Éléments Dynamiques** | 8 | P0 | Plateformes de combat |
| **Effets de Fond** | 6 | P1 | Vortex, distorsions |
| **Phase Transition** | 8 | P1 | Destruction progressive |

**Total Zone 5 :** **38 tiles**

#### 🎨 ÉLÉMENTS VISUELS (VFX/UI)

##### Effets Visuels (Particles/Shaders)

| Effet | Type | Priorité | Notes |
|-------|------|----------|-------|
| **Dust Puff** | Particle | P0 | Landing, dash, run |
| **Jump Trail** | Particle | P1 | Traînée de mouvement |
| **Double Jump Wings** | Sprite + Particle | P0 | Ailes holographiques |
| **Dash Afterimage** | Shader/Sprite | P0 | Fantômes de mouvement |
| **Hit Spark** | Particle | P0 | Impact melee/projectile |
| **Death Dissolve** | Shader | P0 | Dissolution joueur |
| **Glitch Effect** | Shader | P0 | Chromatic aberration, scanlines |
| **Corruption Overlay** | Shader | P1 | Vignette progressive, distorsion |
| **Robot Glow** | Sprite/Shader | P1 | Halo lumineux autour du robot |
| **Checkpoint Activate** | Particle | P1 | Lumière qui s'allume |

##### Interface Utilisateur (UI)

| Élément | Variations | Priorité | Notes |
|---------|------------|----------|-------|
| **Bulle de Dialogue** | 3 (Normal, Suspect, Evil) | P0 | Style arrondi → anguleux |
| **Police de caractères** | 1 | P0 | Pixel font lisible |
| **Boutons Menu** | 4 états (Normal, Hover, Pressed, Disabled) | P0 | |
| **Écran Titre** | 2 (Normal, Post-Reveal) | P1 | |
| **Écran de Fin** | 2 (Corrompue, Pure) | P0 | |
| **Icônes Items** | 3 (Double Jump, Dash, Projectile) | P0 | |
| **Pause Menu** | 1 | P1 | Simple |
| **Transition Fade** | 1 | P0 | Noir |

#### 🔊 AUDIO

##### Musique

| Piste | Zone | Style | Durée | Loop | Priorité | Notes |
|-------|------|-------|-------|------|----------|-------|
| **Main Theme** | Menu | Lo-Fi mélancolique | 1:30-2:00 | Oui | P1 | Accrocheur, mystérieux |
| **Golden Ruins** | Zone 1 | Lo-Fi chaleureux | 2:00-3:00 | Oui | P0 | Synthés doux, guitare |
| **Steel Greenhouse** | Zone 2 | Lo-Fi + touches métalliques | 2:00-3:00 | Oui | P0 | Percussions légères |
| **Reactor** | Zone 3 | Synthwave tendu | 2:00-3:00 | Oui | P0 | Tempo plus rapide |
| **Core** | Zone 4 | Dark Ambient | 2:00-3:00 | Oui | P1 | Drones, malaise |
| **Boss Battle** | Zone 5 | Synthwave intense | 2:00-3:00 | Oui | P0 | Énergie maximale |
| **Corrupted Variant** | Toutes | Distorted versions | - | - | P1 | Pitch shift, glitches audio |
| **True Ending** | - | Calme, résolution | 1:00-1:30 | Non | P0 | Doux, libérateur |
| **Bad Ending** | - | Oppressant | 1:00-1:30 | Non | P0 | Écho, réverbération infinie |

**Total : 8-10 pistes audio**

##### Sound Effects (SFX)

| Catégorie | Son | Priorité | Notes |
|-----------|-----|----------|-------|
| **Mouvement** | Footstep (sol) | P0 | Variations × 3 |
| | Footstep (métal) | P1 | Variations × 3 |
| | Jump | P0 | "Whoosh" satisfaisant |
| | Land | P0 | Impact sourd |
| | Dash | P0 | "Swoosh" rapide |
| | Double Jump | P0 | Son cristallin/holographique |
| | Wall Slide | P0 | Friction |
| | Wall Jump | P0 | Rebond |
| **Combat** | Melee Swing | P0 | "Slash" rapide |
| | Melee Hit | P0 | Impact satisfaisant |
| | Projectile Fire | P0 | Laser/bip |
| | Projectile Hit | P0 | Impact électrique |
| | Player Hurt | P0 | Grunt + impact |
| | Player Death | P0 | Dissolution |
| | Enemy Hurt | P0 | Cri/bruit mécanique |
| | Enemy Death | P0 | Explosion/pop |
| **Robot** | Bip Happy | P0 | Tonalité ascendante |
| | Bip Neutral | P0 | Plat |
| | Bip Suspicious | P1 | Légère dissonance |
| | Bip Glitch | P0 | Modem 56k, distorsion |
| | Bip Evil | P0 | Grave, menaçant |
| | Item Offer | P0 | Chime positif |
| **UI** | Menu Navigate | P0 | Click doux |
| | Menu Confirm | P0 | Validation |
| | Menu Back | P1 | Retour |
| | Dialogue Advance | P0 | Bip texte |
| | Pause | P1 | Freeze sound |
| **Environnement** | Checkpoint | P0 | Activation lumineuse |
| | Door Open | P0 | Mécanique |
| | Trap Activation | P0 | Warning |
| | Ambiance Zone 1-4 | P1 | Layers de fond |
| **Glitch** | Control Hijack | P0 | Distorsion brève |
| | Visual Glitch | P1 | Static burst |
| | Reality Shift | P0 | Transition monde |

**Total estimé : 35-45 SFX**

#### 📊 RÉSUMÉ TOTAL DES ASSETS

| Catégorie | Quantité |
|-----------|----------|
| **Sprites Personnages** | ~180-220 frames |
| **Tilesets** | ~290 tiles (avec variantes) |
| **VFX/Particles** | ~10 systèmes |
| **UI Elements** | ~20-25 éléments |
| **Musiques** | 8-10 pistes |
| **SFX** | 35-45 sons |

---

## Development Epics

### Epic 1 : Core Foundation (Heures 0-8)

| Story | Priorité | Estimation | Acceptance Criteria |
|-------|----------|------------|---------------------|
| Setup projet Godot + structure dossiers | P0 | 30min | Projet compile, dossiers organisés |
| Controller joueur (Move, Jump, Wall Slide) | P0 | 2h | Mouvement fluide, pas de bugs de collision |
| Coyote Time + Jump Buffer | P0 | 30min | Timing tolérant, testable |
| Système de collision + Tilemap de test | P0 | 1h | Collisions précises, pas de clipping |
| Camera follow basique | P0 | 30min | Suivi fluide, pas de jitter |
| Système de mort/respawn instantané | P0 | 1h | Respawn < 0.5s, position correcte |
| **Playtest : Le mouvement est-il satisfaisant ?** | P0 | 30min | Feedback équipe positif |

**Gate :** Le mouvement doit se sentir "tight" avant de continuer.

### Epic 2 : Core Mechanics (Heures 8-20)

| Story | Priorité | Estimation | Acceptance Criteria |
|-------|----------|------------|---------------------|
| Attaque mêlée + hitbox/hurtbox | P0 | 1.5h | Hitreg précis, knockback |
| Double Saut (unlock conditionnel) | P0 | 1h | S'active uniquement si accepté |
| Dash (unlock conditionnel) | P0 | 1h | I-frames, distance fixe |
| Système de Corruption (variable cachée) | P0 | 1h | Incrémente correctement, persiste |
| Glitch de contrôle (input hijack) | P1 | 1.5h | Se déclenche selon corruption |
| Ennemis basiques (patrouille, volant) | P1 | 2h | IA prévisible, tuables |
| Robot compagnon (follow + dialogue trigger) | P0 | 2h | Suit le joueur, déclenche dialogues |
| Système de dialogue (bulles de texte) | P0 | 1.5h | Texte s'affiche, input pour avancer |
| **Playtest : Le choix Facile/Difficile fonctionne ?** | P0 | 30min | Le joueur comprend le dilemme |

**Gate :** La boucle Accept/Refuse doit être claire.

### Epic 3 : Content & Polish (Heures 20-40)

| Story | Priorité | Estimation | Acceptance Criteria |
|-------|----------|------------|---------------------|
| Zone 1 : Ruines Dorées (Tuto) | P0 | 3h | Tutoriel clair, première offre d'objet |
| Zone 2 : Serre d'Acier | P0 | 3h | Verticalité, deuxième offre |
| Zone 3 : Réacteur | P1 | 3h | Dangers environnementaux |
| Zone 4 : Noyau | P2 | 2h | Gauntlet final |
| Boss Room (arène simple) | P1 | 2h | Boss fonctionnel, 2 patterns |
| Dialogues robot (textes + triggers) | P0 | 2h | Tous les dialogues écrits et placés |
| Transition monde Aidé/Corrompu | P1 | 2h | Palette swap ou shader fonctionnel |
| Écrans de fin (2 versions) | P0 | 1h | Fins distinctes selon corruption |
| **Playtest complet : Flow du jeu entier** | P0 | 1h | Jouable du début à la fin |

**Gate :** Le jeu doit être completable avant le polish audio/visuel.

### Epic 4 : Final Build (Heures 40-48)

| Story | Priorité | Estimation | Acceptance Criteria |
|-------|----------|------------|---------------------|
| Menu principal (Start, Quit) | P1 | 1h | Fonctionnel, pas de crash |
| Sound design intégration | P1 | 2h | SFX essentiels en place |
| Musique intégration | P1 | 1h | Au moins 2 pistes (menu + gameplay) |
| Bug fixing critique | P0 | 2h | 0 crash, 0 softlock |
| Polish visuel (particles, juice) | P2 | 1h | Dust puffs, screenshake |
| Build final export | P0 | 30min | .exe fonctionnel |
| Upload Itch.io + page | P0 | 30min | Visible et téléchargeable |

**Gate :** Build stable uploadé avant deadline.

### Priorités Résumé

| Priorité | Signification |
|----------|---------------|
| **P0** | OBLIGATOIRE pour la soumission |
| **P1** | Fortement recommandé si temps disponible |
| **P2** | Nice-to-have, post-jam si possible |

---

## Success Metrics

### Technical Metrics

| Métrique | Cible | Seuil Critique | Méthode de Mesure |
|----------|-------|----------------|-------------------|
| **FPS moyen** | 60 FPS constant | < 55 FPS = bug à fixer | Godot Profiler / Monitor |
| **FPS minimum** | > 55 FPS | < 45 FPS = inacceptable | Test sur scène la plus lourde |
| **Input-to-Action Latency** | < 16ms (1 frame) | < 33ms (2 frames) acceptable | Process dans `_physics_process()` |
| **Temps de respawn** | < 0.5 seconde | < 1 seconde max | Chrono depuis mort → contrôle |
| **Temps de chargement zone** | < 1 seconde | < 2 secondes max | Transition scene |
| **Crashes en session** | 0 | 0 (hard requirement) | Test complet pré-submit |
| **Softlocks** | 0 | 0 (hard requirement) | Playtest toutes les routes |
| **Memory stable** | < 500 MB | Pas de leak sur 30min | Task Manager / Godot Monitor |
| **Build size** | < 100 MB | < 200 MB acceptable | Export final |
| **Startup time** | < 5 secondes | < 10 secondes | Cold start sur SSD |

### Gameplay Metrics

#### Métriques de Progression

| Métrique | Cible | Seuil Acceptable | Note |
|----------|-------|------------------|------|
| **Temps de complétion (Mode Aidé)** | 15-20 min | 12-25 min | Accessible pour les jurés de Jam pressés |
| **Temps de complétion (Mode Pur)** | 30-45 min | 25-60 min | Le vrai challenge |
| **Temps tutorial (Zone 1)** | 2-4 min | 1-5 min | Assez long pour établir la confiance |

#### Métriques de Difficulté

| Métrique | Cible | Note |
|----------|-------|------|
| **Morts moyennes/zone (Aidé)** | 1-3 | Le jeu doit rester accessible avec les pouvoirs |
| **Morts moyennes/zone (Pur)** | 5-10 | Challenge élevé mais jamais injuste |
| **Temps moyen avant premier Game Over** | > 30 sec | Le tutoriel ne doit pas tuer immédiatement |

#### Métriques Narratives (Critiques pour le Twist)

| Métrique | Cible | Importance | Méthode de Validation |
|----------|-------|------------|----------------------|
| **% joueurs qui acceptent le premier objet** | 70-80% | CRITIQUE | Le piège doit fonctionner |
| **% joueurs qui acceptent tous les objets** | 50-60% | Haute | Majorité tombe dans le piège complet |
| **% joueurs qui refusent tout (1ère partie)** | 10-20% | Attendu | Les "méfiants" naturels |
| **% joueurs qui comprennent le twist** | 100% | OBLIGATOIRE | Le reveal doit être clair |
| **Réaction émotionnelle au twist** | Surprise/Trahison | Objectif principal | Playtest qualitatif |

#### Métriques d'Engagement

| Métrique | Cible | Note |
|----------|-------|------|
| **Taux de complétion (Jam judges)** | > 80% | Les jurés doivent finir le jeu |
| **Taux de rejeu pour l'autre fin** | > 30% | Incitation à voir les deux routes |
| **Temps avant premier sourire/réaction** | < 2 min | Le robot doit charmer rapidement |

---

## Out of Scope

Les éléments suivants sont **explicitement exclus** du scope de la Game Jam pour protéger les 48 heures de développement :

### Features Exclues

| Feature | Raison | Post-Jam ? |
|---------|--------|------------|
| ❌ **Mode Multijoueur** | Complexité réseau, temps de debug | Non |
| ❌ **Sauvegarde persistante** | Jeu court (15-45 min), inutile | Peut-être |
| ❌ **Système d'inventaire** | Trop de UI, les objets sont binaires (oui/non) | Non |
| ❌ **Plus de 5 zones** | Scope trop large pour 48h | Oui |
| ❌ **Plus de 2 fins** | 2 fins suffisent pour le message narratif | Peut-être |
| ❌ **Dialogues branchés complexes** | Temps d'écriture, le robot parle linéairement | Oui |
| ❌ **Arbre de compétences** | Overcomplexe, les unlocks sont simples | Non |
| ❌ **Système de crafting** | Hors concept | Non |

### Plateformes Exclues

| Plateforme | Raison | Post-Jam ? |
|------------|--------|------------|
| ❌ **Web (HTML5)** | Bugs d'export Godot 4 fréquents sous pression | Oui |
| ❌ **Mobile (iOS/Android)** | Contrôles tactiles = refonte UI | Peut-être |
| ❌ **Console (Switch/PS/Xbox)** | Certification, devkits | Oui (si succès) |
| ❌ **Linux** | Test insuffisant en 48h | Oui |
| ❌ **Mac** | Test insuffisant en 48h | Oui |

### Accessibility Exclue (Temporairement)

| Feature | Raison | Post-Jam ? |
|---------|--------|------------|
| ❌ **Remapping des touches** | Temps UI | Oui |
| ❌ **Mode daltonien** | Shaders additionnels | Oui |
| ❌ **Sous-titres audio descriptifs** | Temps d'écriture | Oui |
| ❌ **Mode "Assist" (invincibilité)** | Contradictoire avec le message du jeu | À débattre |

### Contenu Exclu

| Contenu | Raison |
|---------|--------|
| ❌ **Lore écrit (journaux, notes)** | Le lore est environnemental uniquement |
| ❌ **Cutscenes animées** | Trop de temps de production |
| ❌ **Voix off / Voice acting** | Budget/temps |
| ❌ **Trailer vidéo** | Post-Jam |

### Polish Exclu (Si manque de temps)

| Élément | Priorité réelle |
|---------|-----------------|
| ⚠️ Screenshake | P2 - Coupable en premier |
| ⚠️ Particles de run | P2 |
| ⚠️ Transition fondu entre zones | P2 |
| ⚠️ Musique Zone 4 distincte | P2 - Réutiliser Zone 3 si besoin |

---

## Assumptions and Dependencies

### Hypothèses Techniques

| Hypothèse | Impact si Fausse | Plan B |
|-----------|------------------|--------|
| **Godot 4.3+ est stable pour platformer 2D** | Bugs de physique/collision | Rollback Godot 4.2 LTS ou 3.5 |
| **CharacterBody2D fonctionne pour le mouvement** | Glitches de collision | Utiliser KinematicBody custom |
| **Export Windows .exe fonctionne** | Pas de build jouable | Test export dès H+4 |
| **Shaders simples (palette swap) tournent à 60fps** | Lag visuel | Désactiver effets, sprites swap manuels |
| **TileMap Godot 4 est fonctionnel** | Level design bloqué | Sprites individuels positionnés à la main |

### Hypothèses de Production

| Hypothèse | Impact si Fausse | Plan B |
|-----------|------------------|--------|
| **Assets pixel art créables dans le temps** | Visuel incomplet | Placeholders carrés colorés (fonctionnel > joli) |
| **Musique Lo-Fi trouvable/créable** | Pas d'audio | Assets libres (OpenGameArt, FreePD, Incompetech) |
| **SFX basiques réalisables** | Silence gênant | BFXR/SFXR pour génération rapide |
| **Un seul développeur peut tout faire** | Burnout, scope overflow | Couper Zone 4, réduire à 3 zones + boss |

### Hypothèses de Design

| Hypothèse | Impact si Fausse | Plan B |
|-----------|------------------|--------|
| **Le twist narratif est compréhensible** | Message raté | Dialogue explicite du robot à la fin |
| **Le choix Accept/Refuse est clair** | Confusion joueur | Popup UI "Accepter? [Oui/Non]" explicite |
| **Les joueurs font confiance au robot** | Piège ne fonctionne pas | Rendre robot ENCORE plus mignon/utile |
| **La difficulté "Pure" est faisable** | Frustration, abandon | Ajouter checkpoint secret mid-zone |
| **Le respawn instantané suffit** | Rage quit | Option "Skip Room" après 10 morts (mode assist caché) |

### Dépendances Logicielles

| Dépendance | Version | Criticité | Alternative |
|------------|---------|-----------|-------------|
| **Godot Engine** | 4.3+ | OBLIGATOIRE | 4.2 LTS, 3.5 |
| **GDScript** | Natif | OBLIGATOIRE | - |
| **Aseprite** | Dernière | Haute | Piskel (gratuit), Photoshop |
| **Audacity** | Dernière | Moyenne | Reaper, online tools |
| **BFXR/SFXR** | Web/Desktop | Moyenne | Freesound.org |
| **Git** | Dernière | Haute | Backup manuel (risqué) |

### Dépendances Externes

| Dépendance | Criticité | Note |
|------------|-----------|------|
| **Compte Itch.io** | OBLIGATOIRE | Pour upload final |
| **Connexion Internet stable** | Haute | Upload build, assets si besoin |
| **PC de dev fonctionnel** | CRITIQUE | Pas de backup hardware |
| **Électricité stable 48h** | CRITIQUE | 🙏 |

### Dépendances Humaines

| Dépendance | Criticité | Mitigation |
|------------|-----------|------------|
| **Santé développeur** | CRITIQUE | Pauses obligatoires, sommeil minimum 4-6h |
| **Motivation constante** | Haute | Milestones clairs, célébrer les petites victoires |
| **Pas de distractions majeures** | Haute | Mode focus, notifications off |

### Risques Identifiés

| Risque | Probabilité | Impact | Mitigation |
|--------|-------------|--------|------------|
| **Scope creep** | Haute | Critique | Liste Out of Scope stricte |
| **Bug bloquant à H-4** | Moyenne | Critique | Feature freeze à H-8 |
| **Fatigue créative** | Haute | Haute | Zone 4 en dernier, coupable si besoin |
| **Le twist ne fonctionne pas** | Moyenne | Haute | Playtest H+20, ajuster dialogues |
| **Pas assez de contenu** | Moyenne | Haute | 3 zones minimum = viable |
| **Trop de contenu, pas de polish** | Moyenne | Moyenne | Polish > Contenu après H+35 |
