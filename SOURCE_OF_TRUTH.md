# Clone Lab Idle — Source of Truth

> Canonical product and gameplay specification. When implementation details conflict with this document, update this document deliberately before changing the game.

## Project identity

- **Name:** Clone Lab Idle
- **Format:** Incremental / idle boss-fighting game
- **Primary platform:** iPhone browser (Safari), portrait-first
- **Secondary platform:** Desktop browser, responsive layout
- **Hosting target:** GitHub Pages
- **Visual genre:** 2D pixel-art management simulation, inspired by the charm, scale, and readable presentation of Kairosoft-style games
- **Core fantasy:** Build and upgrade a cloning laboratory that manufactures tiny warriors to automatically fight increasingly powerful bosses.

## Core experience

The player manages one laboratory room. A large boss occupies the central combat area. A cloning machine sits in the bottom-right area and is the primary progression interface. The player improves the machine, produces warriors, watches them emerge, and lets them fight automatically.

The laboratory should feel like a small, lively simulation that the player is observing—not a conventional RPG battle menu or a static upgrade screen.

## Main gameplay loop

1. The player opens the cloning machine interface by tapping the machine.
2. The player spends the appropriate currency on machine upgrades.
3. Production upgrades increase clone output, production cadence, or the number of clones produced per cycle.
4. Clone-type upgrades unlock additional warrior classes or variants.
5. When an upgrade or production action creates a clone, the machine plays a readable production sequence.
6. A newly produced warrior emerges from the machine, enters the room, and automatically approaches and attacks the active boss.
7. Warriors continue fighting without requiring individual player commands.
8. When the boss is defeated, its death animation plays to completion.
9. The player receives the boss reward, and the next boss enters or appears.
10. The player reinvests rewards into production and stronger clone types.

Boss progression must be sequential: do not spawn the next boss over the previous boss before its defeat/death sequence has completed.

## Primary screen composition

The main play area is one large, bright laboratory room.

- **Boss:** Large and visually dominant near the center of the room. Show a readable boss name and health bar without obscuring the room.
- **Cloning machine:** Anchored in the bottom-right of the room. It must remain easy to identify and tap.
- **Warriors:** Small characters produced by the machine. They occupy the room and visibly engage the boss.
- **HUD:** Currency, current boss/progression, and essential production/combat information. Keep it compact so the room remains the focus.
- **Machine upgrade interface:** Opens when the machine is tapped. It should feel attached to the machine and expose production and clone-type upgrades without permanently covering the battle.

Exact screen coordinates may adapt to device dimensions, but the relative hierarchy and visual relationships above are canonical.

## Cloning machine progression

The cloning machine is the player's central upgrade system.

Upgrade families:

- **Production quantity:** More warriors produced per cycle or more warriors in a production batch.
- **Production rate:** Shorter time between production cycles.
- **Clone unlocks:** New warrior types/classes become available.
- **Clone improvements:** Where appropriate, improve the strength or effectiveness of unlocked warriors.

An upgrade that creates or unlocks a clone must provide clear feedback. The player should understand what was purchased, what appeared, and how it changes the army. Avoid upgrades that silently change the game state.

The exact upgrade names, costs, scaling curves, class roster, and balance values are implementation decisions to be tuned during playtesting. Keep these values data-driven rather than scattering them through rendering code.

## Combat rules

- Combat is automatic after a warrior is produced.
- Warriors should visibly travel from the machine area toward the boss before attacking, rather than simply appearing in a battle formation.
- Warriors need readable idle/movement/attack/defeat states as supported by the chosen art assets.
- The boss has health and a clear defeat state.
- The boss should react to incoming attacks where practical.
- Boss death is a distinct sequence; rewards and the next boss follow that sequence.
- The game should communicate progress even when many warriors are present. Avoid visual effects that make the boss, warriors, or room unreadable.

## Idle and incremental expectations

The game should reward both active interaction and letting the simulation run.

- Production and combat should proceed automatically after upgrades are purchased.
- Progression should be incremental and understandable: the player can see how each machine upgrade improves output or unlocks new options.
- Save player progress locally in the browser so a refresh does not erase the run.
- Use elapsed-time/offline progress only when it can be implemented reliably and capped sensibly; never grant duplicate or implausible rewards after clock changes or long absences.
- Keep core game state separate from UI rendering so balancing and saving remain reliable.

## Mobile-first interaction requirements

- Portrait iPhone Safari is the primary target.
- The room and important controls must fit the viewport without requiring awkward horizontal scrolling.
- Interactive targets, especially the cloning machine and upgrade controls, must be comfortable to tap.
- Upgrade panels should scroll internally when needed; avoid making the entire game screen unexpectedly scroll.
- Respect iPhone safe areas and browser viewport changes.
- Keep text legible at phone size and avoid relying on hover interactions.
- Desktop layouts may use additional space but must preserve the same visual hierarchy and game rules.

## Technical direction

- Target a lightweight browser implementation suitable for GitHub Pages.
- Prefer HTML, CSS, and JavaScript unless the project establishes a clear reason to add a framework or build step.
- Keep game data (boss definitions, clone definitions, upgrade definitions, costs, and balance values) separate from simulation and presentation logic.
- Use deterministic, testable functions for economy, production, combat, rewards, and save migration where practical.
- Do not make the game dependent on a server for its basic idle loop or local save.
- Preserve mobile performance: limit unnecessary DOM churn, expensive effects, and excessive simultaneous animation work.

## Product guardrails

- The laboratory remains a bright, predominantly white indoor room—not a dark dungeon, outdoor battlefield, or generic menu background.
- The cloning machine is the main player-facing upgrade hub and stays in the bottom-right region of the room.
- The boss is the central encounter and stays visually prominent.
- Warriors are tiny pixel-art RPG-style characters created by the machine.
- The core loop remains machine upgrades → clone production → automatic boss combat → boss reward → next boss.
- Do not add unrelated systems that compete with this central loop before the core loop is satisfying.
- Do not replace the room simulation with a conventional turn-based battle screen.

## Initial milestone definition

The first playable milestone should establish:

1. A responsive portrait-first laboratory room.
2. One visible boss with a health bar.
3. A visible cloning machine with a tappable upgrade interface.
4. At least one production upgrade that creates a warrior.
5. A clear machine production animation and warrior emergence.
6. Automatic warrior movement and attacks against the boss.
7. A boss defeat animation, reward, and next-boss transition.
8. Persistent local progress.
9. A usable desktop layout.

Additional clone types, larger boss rosters, deeper upgrade trees, offline progression, and polish follow after this loop works reliably.

## Change control

This file is the canonical source of truth for product behavior and scope. When a new decision changes the core loop, screen composition, platform target, or progression rules, update this file as part of that implementation. Record visual and asset-specific rules in `ART_SOURCE.md`.
