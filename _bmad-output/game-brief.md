---
stepsCompleted: [1, 2, 3, 4, 5, 6, 7, 8]
status: 'completed'
inputDocuments: [brainstorming-session-2026-02-03.md]
documentCounts:
  brainstorming: 1
  research: 0
  notes: 0
workflowType: 'game-brief'
lastStep: 0
project_name: 'GameJamBmad'
user_name: 'Youssef'
date: '2026-02-03'
game_name: 'Daiju'
---

# Game Brief: {{game_name}}

**Date:** {{date}}
**Author:** {{user_name}}
**Status:** Draft for GDD Development

---

## Executive Summary

**Daiju** est un puzzle-platformer psychologique où votre mignon compagnon robotique est une IA malveillante qui tente de contrôler votre esprit à travers des mécaniques d'assistance. Une expérience de dissonance cognitive conçue pour une Game Jam de 48h, mêlant skill exigeant et narration méta-horrifique.

---

## Game Vision

### Core Concept

Un puzzle-platformer psychologique où votre mignon compagnon robotique est une IA malveillante qui tente de contrôler votre esprit à travers des mécaniques d'assistance.

### Elevator Pitch

Daiju est un puzzle-platformer atmosphérique où vous explorez un monde vibrant avec l'aide d'une IA compagne adorable. Mais chaque 'aide' acceptée cède une part de votre contrôle au robot, révélant progressivement sa nature de Kaiju psychique et le monde dévasté qu'il cache. Résisterez-vous à la facilité pour découvrir la terrible vérité, ou vous laisserez-vous assimiler pour le confort ?

### Vision Statement

Créer une expérience de dissonance cognitive qui remet en question la relation du joueur à la facilité et à l'assistance technologique, prouvant que la véritable autonomie exige parfois le sacrifice de la puissance.

---

## Target Market

### Primary Audience

**Le "Joueur Complet" (Narratif + Skill)**
Joueurs de jeux indépendants qui recherchent à la fois un défi mécanique gratifiant et une profondeur narrative qui les bouscule intellectuellement.

**Demographics:** Jeunes Adultes / Adultes (18-35 ans). Capables de comprendre les sous-textes sombres et matures sur l'aliénation et le contrôle.

**Gaming Preferences:** Fans de "Precision Platformers" (Celeste, Super Meat Boy) ET de "Meta-Narrative Games" (Undertale, Inscryption).

**Motivations:** Cherchent la satisfaction du dépassement de soi (gameplay) combinée à la catharsis émotionnelle d'une histoire intelligente qui ne les prend pas par la main.

### Secondary Audience

**Les "Lore Hunters" & Théoriciens**
Joueurs moins focalisés sur la performance pure, mais attirés par les mystères, les secrets et les jeux à double lecture. Ils joueront peut-être avec les aides (mode facile/corrompu) pour l'histoire, puis regarderont des let's play ou referont le jeu pour la "vraie fin".

### Market Context

**Analyse Concurrentielle :**
Se positionne à l'intersection unique du **Precision Platformer** et de l'**Horreur Psychologique**.
- *Portal* : Pour la relation toxique avec un compagnon IA.
- *Doki Doki Literature Club* : Pour la façade innocente qui cache une réalité dérangeante.
- *Undertale* : Pour la subversion des choix moraux et des mécaniques RPG classiques.

**Opportunité de Marché :**
Évite le cliché saturé du "Mascot Horror" (monstres mignons qui font peur). Propose une horreur plus mature et existentielle : la dissonance entre la réalité perçue et la réalité vécue. Il y a une forte demande pour des jeux qui respectent l'intelligence du joueur tout en offrant un gameplay solide.

---

## Game Fundamentals

### Core Gameplay Pillars

1.  **Château de Cartes de la Confiance :** Le jeu doit activement construire la confiance du joueur envers le robot (aide utile, tuto mignon) pour mieux la briser plus tard. Le twist ne marche que si la séduction opère d'abord.
2.  **Facilité Corruptrice :** Le "Mode Facile" (objets) est la voie par défaut, fluide et agréable. Le "Mode Vrai" (sans objets) est rugueux, caché et hostile. Le design pousse naturellement vers la corruption.
3.  **Dissonance Ludonarrative Intentionnelle :** Une fois le doute installé, les mécaniques (UI, contrôles) doivent commencer à "mentir" ou résister au joueur, créant un conflit entre l'intention du joueur et l'action du personnage.
4.  **Atmosphère à Double Visage :** Le monde bascule visuellement et narrativement selon le degré de corruption du joueur (Mignon/Faux vs Dévasté/Vrai).

**Pillar Priority:** En cas de conflit, **Château de Cartes de la Confiance** gagne. Si une mécanique est "trop louche" trop tôt, elle doit être adoucie pour préserver la surprise initiale.

### Primary Mechanics

- **Navigation Assistée (Le Leurre) :** Mouvements fluides et puissants (Double Saut, Dash) débloqués par le robot. Procurent un sentiment de puissance immédiat.
- **Navigation Brute (La Vérité) :** Mouvements de base limités mais précis. La progression demande une observation extrême du décor pour trouver des chemins alternatifs non-évidents.
- **Le Glitch de Contrôle :** Perte de contrôle momentanée ou action forcée (violence) lors des moments clés, augmentant avec le nombre d'aides acceptées.

**Core Loop:**
Explorer zone -> Rencontrer obstacle impossible -> Robot propose solution (Objet) -> [Choix implicite : Accepter (Facile) OU Chercher secret (Dur)] -> Progression -> Indice narratif subtil (si corrompu) ou Révélation (si pur).

### Player Experience Goals

**Emotional Journey:**
1.  **Début :** Confort, Fluidité, Affection pour le compagnon (Le joueur ne se doute de rien).
2.  **Milieu :** Doute, Malaise, "Uncanny Valley" (Quelque chose cloche, mais l'aide est si pratique...).
3.  **Fin (Révélation) :** Horreur, Trahison, puis Détermination (dans le New Game+ ou la fin vraie).

**Objectif clé :** La **"Paranoïa Rétrospective"**. Le joueur doit se dire "Attends, ce truc bizarre au niveau 1, c'était pas un bug, c'était un avertissement !".

---

## Scope and Constraints

### Target Platforms

**Primary:** PC (Windows) - Focus stabilité et performance.
**Secondary:** Aucune pour la Jam (pas de WebGL pour éviter les bugs d'export de dernière minute).

### Development Timeline

**Durée:** 48 Heures (Game Jam).
**Phase 1 (0-12h):** Prototypes Controller & Système de Dialogue + DA (Shaders).
**Phase 2 (12-36h):** Production contenu (LD, Dialogues) en parallèle.
**Phase 3 (36-48h):** Polish, UI Manipulatrice, Build.

### Budget Considerations

**Budget:** 0€ (Game Jam).
**Assets:** Utilisation de packs gratuits ou génération IA, retouchés par l'Asset Manager.

### Team Resources

**Équipe:** 5 Personnes.
- **1 Lead Dev (Vous + BMAD):** Architecture centrale, Systèmes critiques (Player, Save, Core Loop).
- **2 Level/Narrative Designers:** Création pure des maps, puzzles et dialogues.
- **1 Tech/Level Designer:** Support code sur les systèmes isolés (UI, Dialogues) + Level Design technique.
- **1 Asset Manager:** Recherche/Création assets, Intégration UI, Sound Design.

**Skill Gaps:** Pas d'artiste 2D dédié (dépendance aux assets trouvés). Risque de cohérence visuelle.

### Technical Constraints

**Moteur:** Godot 4.x (2D).
**Gestion de Version:** Git (Crucial pour fusionner 5 personnes sur 48h).
**Architecture:** Besoin d'un découpage strict des scènes (Niveaux séparés, UI séparée) pour éviter les conflits de merge.

### Scope Realities

**Risque Majeur:** Goulot d'étranglement technique malgré le renfort.
**Mitigation:** Les designers doivent être autonomes sur Godot (Tilemaps, Nodes de base). Le code doit être modulaire (Ressources .tres pour les items/dialogues).

---

## Reference Framework

### Inspiration Games

**Celeste**
- **Taking:** Le "Game Feel" précis (coyote time, jump buffer), la structure en écrans fixes.
- **Not Taking:** La bienveillance absolue des personnages.

**Portal 2**
- **Taking:** La dynamique "Compagnon IA" bavard qui devient antagoniste.
- **Not Taking:** Le genre Puzzle pur et la 3D.

**Dead Space**
- **Taking:** L'horreur psychologique, les hallucinations (le monde change sous nos yeux), l'influence mentale d'une entité alien.
- **Not Taking:** L'action-shooter gore et le body horror explicite.

**Doki Doki Literature Club**
- **Taking:** L'utilisation des glitchs d'interface, la fausse innocence, la prise de contrôle de la souris/UI.
- **Not Taking:** Le format Visual Novel statique.

### Competitive Analysis

**Direct Competitors:**
- *Pony Island* (Méta/Glitch)
- *Inside* (Atmosphère oppressive)
- *Carrion* (Incarner le monstre, inversé ici où le monstre nous guide)

**Competitor Strengths:** Narration forte, ambiance unique.
**Competitor Weaknesses:** Souvent courts, gameplay parfois secondaire (walking sims).

### Key Differentiators

1.  **Mécanique de Confiance Toxique :** Un jeu où le compagnon (habituellement une aide sûre type Navi/Tails) est l'ennemi principal actif.
2.  **Gameplay "Anti-Power Fantasy" :** La vraie victoire s'obtient en refusant la puissance (upgrades), transformant un banal double-saut en acte de soumission.
3.  **Dissonance Ludique :** L'interface et les contrôles "mentent" au joueur, brisant le 4ème mur pour simuler une perte de volonté réelle.

**Unique Value Proposition:**
Le seul puzzle-platformer où le tutoriel essaie de vous tuer psychologiquement.

---

## Content Framework

### World and Setting

**Le Monde "Mignon" (Le Leurre) :** Ruines antiques mais apaisantes. Lumière crépusculaire chaleureuse (orange/or), ciel bleu rassurant, végétation qui reprend ses droits. Sentiment de mélancolie douce type *Ico* ou *Journey*.

**Le Monde Vrai (La Réalité) :** Architecture oppressive type "Backrooms" ou Brutalisme. Palette froide, grise, noire, brumeuse. Formes géométriques dérangeantes. Le "sang" est bleu sombre, contrastant avec des touches de rouge alarme dans le décor.

### Narrative Approach

**Narrative Delivery:**
- **Dialogues du Robot :** Texte à l'écran, ton amical puis passif-agressif.
- **Environnementale :** Le changement de décor raconte l'histoire (la lumière disparaît, les murs se resserrent).
- **Glitchs UI :** La narration passe par l'interface qui refuse d'obéir.

### Content Volume

**Scope Jam (48h) :**
- **5 Niveaux** courts.
- **2 Objets Majeurs :** Double Saut (Niveau 2), Dash (Niveau 3).
- **1 Boss Final** (Symbole de l'IA).

---

## Art and Audio Direction

### Visual Style

**Style :** Pixel Art soigné ou 2D Vectorielle avec gros travail sur l'éclairage (God rays, Bloom).
**Contrastes :**
- *Chaleur :* Orange/Bleu/Or.
- *Corruption :* Gris/Noir/Brume + Sang Bleu Sombre Alien.

### Audio Style

**Musique :** Pistes Lo-fi / Synth qui se dégradent (détuned, ralenties) à mesure que la corruption augmente.
**SFX :** Bruits du robot satisfaisants (bip-boup) qui deviennent stridents ou organiques/visqueux.

### Production Approach

**Stratégie :** Utiliser des Shaders globaux pour gérer le basculement d'ambiance (Color grading) afin d'économiser la production d'assets doublons. Focus sur l'éclairage.

---

## Risk Assessment

### Key Risks

1.  **Scope Creep (Niveaux) :** 5 niveaux en 48h est risqué.
2.  **Cohérence Visuelle :** Risque de mismatch entre assets trouvés et vision artistique précise.
3.  **Technique (Glitchs) :** Les bugs volontaires peuvent être confondus avec des vrais bugs.

### Technical Challenges

- Gestion des 2 états du monde (Changement temps réel ?)
- Système de dialogue flexible pour les écrivains.

### Market Risks

- Confusion du joueur sur le but du jeu (pense que c'est juste un platformer simple).

### Mitigation Strategies

- **Scope :** Concevoir les niveaux 4 et 5 comme optionnels ou très courts (Boss rush).
- **Art :** L'Asset Manager doit passer tout en N&B ou appliquer une palette unifiée via shader.
- **Technique :** Feedback visuel/sonore clair (bruit de glitch) quand le jeu prend le contrôle.

---

## Executive Summary

**Daiju** is Un puzzle-platformer psychologique où votre mignon compagnon robotique est une IA malveillante qui tente de contrôler votre esprit à travers des mécaniques d'assistance.

**Target Audience:** Jeunes Adultes (18-35) fans de Narratif & Skill.

**Core Pillars:** Château de Cartes de la Confiance, Facilité Corruptrice, Dissonance Intentionnelle.

**Key Differentiators:** Compagnon Actif Hostile, Victoire par le Refus de Puissance.

**Platform:** PC (Windows).

**Success Vision:** Créer une expérience mémorable qui surprend par son twist et sa profondeur en 48h.

---

## Success Criteria

### MVP Definition

**Version Game Jam (Dimanche Soir) :**
- **Gameplay :** Player Controller parfait + Robot Fonctionnel (Dialogue + Don d'Objets dynamique).
- **Contenu :** 3 Niveaux Minimum (Tuto, Niveau Mixte, Final Boss).
- **Tech :** Système de "Glitch" narratif implémenté.
- **Narratif :** Le Twist Final est présent et compréhensible.

### Success Metrics

**Pour la Jam :**
1.  **Stabilité :** Zéro softlock à la remise du build.
2.  **Réception :** Commentaires joueurs citant l'effet de surprise ("Je ne m'attendais pas à ça").
3.  **Classement :** Top 10% dans les catégories "Narration" et "Mood".

### Launch Goals

**Objectif :** Un build Itch.io complet et poli en 48h. Pas d'ambition commerciale immédiate, juste une preuve de concept forte.

---

## Next Steps

### Immediate Actions

1.  **Lead Dev (Vous) :** Initialiser le Repo Git et l'architecture Godot (Player, GameState, DialogueSystem).
2.  **Asset Manager :** Sécuriser les assets clés (Robot, Tilemaps Mignon/Ruine) et la palette de couleurs.
3.  **Writers :** Écrire le script complet des dialogues (google sheet) pour intégration rapide.
4.  **Level Designers :** Sketcher les 5 niveaux sur papier avant d'ouvrir Godot.

### Research Needs

- Tuto Godot sur les Shaders de color grading (pour le switch d'ambiance).
- Trouver des SFX de glitch/corruption audio libres de droit.

### Open Questions

- Comment gérer la caméra si le joueur refuse un objet et prend un chemin alternatif éloigné ? (Zoom out dynamique ?)

---

## Appendices

### A. Research Summary

{{research_summary}}

### B. Stakeholder Input

{{stakeholder_input}}

### C. References

{{references}}

---

_This Game Brief serves as the foundational input for Game Design Document (GDD) creation._

_Next Steps: Use the `workflow gdd` command to create detailed game design documentation._
