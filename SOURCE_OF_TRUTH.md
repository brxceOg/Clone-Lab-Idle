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

The player manages one laboratory room. A large boss occupies the central combat area. A cloning machine sits in the bottom-right area and is the primary progression interface. The player improves the machine from a dedicated UPGRADES button in the bottom-left of the lab, watches warriors emerge from the machine in the bottom-right, and lets them fight automatically.

The laboratory should feel like a small, lively simulation that the player is observing—not a conventional RPG battle menu or a static upgrade screen.

## Main gameplay loop

1. The player opens the upgrade interface with the dedicated UPGRADES button in the bottom-left of the lab.
2. The player spends the appropriate currency on production and clone upgrades in the upgrade panel.
3. The machine produces clones automatically on its own cycle; the player never presses a manual produce button. Production upgrades increase output, cadence, or batch size.
4. Clone-type upgrades unlock additional warrior classes or variants.
5. When an upgrade or production action creates a clone, the machine plays a readable production sequence.
6. A newly produced warrior emerges from the machine, enters the room, and automatically approaches and attacks the active boss. Melee classes close to the boss; ranged classes maintain a sensible firing distance.
7. Warriors continue fighting without requiring individual player commands. They move as a coordinated army while maintaining personal space through soft crowd-separation steering.
8. Boss attacks damage nearby clones and give survivors a very small, brief outward nudge (about 10–13 room pixels total) with a hit-spark cue; survivors settle back into their assigned formation slots almost immediately, without disrupting the formation. A defeated clone is placed in the machine replacement queue and automatically respawned after a short production delay. The machine maintains the army toward its current active-clone capacity, reserving space for queued replacements so it cannot overfill the room or strand a replacement queue. The Clone Capacity upgrade permanently raises that cap by 5 clones per purchase.
9. When the boss is defeated, its death animation plays to completion.
10. The player receives the boss reward, and the next boss enters or appears.
11. The player reinvests rewards into production and stronger clone types.

Boss progression must be sequential: do not spawn the next boss over the previous boss before its defeat/death sequence has completed.

## Endless boss progression and difficulty scaling

- The 14 existing boss appearances repeat in their established order; reusing a sprite does not reset encounter progression or difficulty.
- Preserve the authored opening health curve for the first 14 encounters: 100, 180, 280, 430, 620, 900, 1,280, 1,800, 2,500, 3,500, 4,900, 6,800, 9,400, and 13,000 health.
- After the first full roster, each new encounter starts from the previous roster's 13,000-health benchmark and increases maximum boss health by 18% per defeat. This calculation is based on the lifetime encounter index, never the position within the repeating roster.
- Bosses also become gradually more relentless: their attack interval shortens by 1.8% per encounter, with a 1.9-second minimum so attacks remain readable and playable.
- Existing local saves retain their current boss encounter and health progress proportionally when the new scaling is applied. The encounter index remains the source of truth for future scaling.
- Boss rewards continue to scale with encounter progression so later victories remain worthwhile.

## Primary screen composition

The main play area is one large, bright laboratory room.

- **Boss:** Large and visually dominant near the center of the room. Show a readable boss name and health bar without obscuring the room. The boss name and health bar render in the final foreground layer above all clone sprites and combat effects, so units can never cover the bar.
- **Cloning machine:** Anchored in the bottom-right of the room. It must remain easy to identify and tap.
- **Warriors:** Small characters produced by the machine. They occupy the room and visibly engage the boss.
- **HUD:** Currency, current boss/progression, and essential production/combat information. Keep it compact so the room remains the focus.
- **Upgrade interface:** Opens from a dedicated UPGRADES button anchored at the bottom-left of the lab. It exposes production and clone-type upgrades without permanently covering the battle. Tapping the cloning machine itself does not open the panel.

Exact screen coordinates may adapt to device dimensions, but the relative hierarchy and visual relationships above are canonical.

## Cloning machine progression

The cloning machine is the player's central upgrade system.

Upgrade families:

- **Production quantity:** More warriors produced per cycle or more warriors in a production batch.
- **Production rate:** Shorter time between production cycles.
  - The Production cycle upgrade starts at 35 credits and scales by 1.5× for every purchase using a saved purchase level. Existing saves infer that level from their current production interval. The upgrade stops accepting purchases at the 1.5-second minimum.
- **Clone unlocks:** New warrior types/classes become available.
- **Clone improvements:** Where appropriate, improve the strength or effectiveness of unlocked warriors.

### Combat and survivability upgrade paths

- The Combat Systems path is sequential: Combat Systems is its first node, Divine Intervention is the second, Attack Speed is the third, and Double Hit Chance is directly below Attack Speed as the fourth node. Divine Intervention cannot be purchased until Combat Systems is unlocked; Attack Speed cannot be purchased until Divine Intervention is unlocked; Double Hit Chance cannot be purchased until Attack Speed is unlocked.
- Double Hit Chance starts at a 12% chance and increases by 4 percentage points per level, capped at 40%. Only regular Knight clones can trigger it; summoned Skeletons, Mages, Archers, and Necromancers are excluded. After a Knight's normal strike lands, a successful proc delivers one clearly signaled follow-up strike after a short 150 ms beat. The bonus strike uses the same 1.15× Knight damage and earns the normal per-strike credits, but it does not modify or reset the Knight's regular attack cooldown.
- Divine Intervention gives a clone that would otherwise be defeated by a boss attack a 20% chance to revive immediately at half of its current maximum health. Each additional level adds 10 percentage points, capped at 75%. A successful revival prevents the normal defeat/replacement queue for that hit.
- Attack Speed reduces the time between clone attacks by 8% per level, applied multiplicatively. Cooldowns have a 420 ms minimum to preserve readable combat timing.
- A separate Clone Health path branches from the lower-left side of the core, opposite Credit Yield. Each level increases every clone's base maximum health by 1 HP; existing active clones gain the same 1 HP immediately, and future/restored clones use the upgraded base health.
- Persist Divine Intervention, Attack Speed, Double Hit Chance, and Clone Health levels in the local save. Older saves default the new Double Hit Chance level to zero and retain their existing progression.

An upgrade that creates or unlocks a clone must provide clear feedback. The player should understand what was purchased, what appeared, and how it changes the army. Avoid upgrades that silently change the game state.

The exact upgrade names, costs, scaling curves, class roster, and balance values are implementation decisions to be tuned during playtesting. Keep these values data-driven rather than scattering them through rendering code.

## Combat rules

- Combat and production are automatic. The player does not manually spawn or produce clones.
- Boss attacks must damage clones; defeated clones are automatically replaced by the cloning machine after a short delay.
Mage magic missiles and Archer arrows use explicit projectile events with launch positions based on each ranged clone's current coordinates and interpolated travel independent of the source sprite's built-in movement. Calculate flight duration from the actual visible launch-to-impact anchor distance at a fixed projectile speed; never cap flight duration by distance. Keep each projectile alive and visible until it reaches its destination, even if its sprite asset is unavailable (draw the simple pixel fallback projectile instead of discarding the event). On arrival, always trigger a visible impact: use the Mage arcane burst or Archer hit-spark when available, plus the small guaranteed pixel impact burst. Archer arrows target two room pixels inside the boss's rendered outer radius. Mage missiles target a point at 42% of the boss radius from its center so the visible missile head and arcane impact clearly overlap the boss silhouette, including sprites with transparent outer margins. Archer arrows use frame 3 of the arrow-impact asset: its visible tail is 18 source pixels behind the manifest pivot and the arrowhead tip is 10 source pixels ahead. Start the visible tail 7 room pixels forward of the Archer's center (at the bow/hand edge), align the draw pivot 18 × projectile scale ahead of that tail, and finish with the arrowhead tip exactly at the impact target by placing the final pivot 10 × projectile scale behind the target. Mage missiles use frame 10 of the magic-missile asset: its visible tail is approximately 32 source pixels behind the manifest pivot and its leading tip is approximately 21 pixels ahead. Start the visible tail 7 room pixels forward of the Mage's center (at the casting-hand edge), align the draw pivot 32 × projectile scale ahead of that tail, and finish with the leading tip exactly at the impact target by placing the final pivot 21 × projectile scale behind the target. Interpolate between independently calculated launch and impact anchors for both projectile types. Draw projectiles in the foreground while they travel; trigger an arrow hit-spark or Mage arcane burst at the exact destination on arrival. Keep projectile visual arrival and combat damage feedback synchronized; do not use one shared pivot offset for both ends.
- Melee units approach the boss closely before attacking. All melee clones and summoned Skeletons first use the same compact inner formation ring and stable slot ordering to gather around the boss. Once the currently deployed melee group has finished gathering in its assigned inner-ring positions, the group transitions into a continuous close-range bee-like swarm: units circle and buzz around the boss with individually varied directions, speeds, and small radial fluctuations. A newly produced clone or newly emerged Skeleton joins the existing swarm only after reaching its own assigned gathering position. The swarm stays tightly constrained to the boss perimeter and never scatters across the room. Mage, Archer, and Necromancer clones retain their existing ranged formation mentality: they approach their assigned outer slots (about 28 room pixels beyond the melee ring), then hold those positions and do not join the swarm. Stable formation-slot indices remain unchanged when another clone is produced, defeated, or respawned.
- Do not apply crowd-separation steering that pushes units away from the boss. Boss strikes retain the small outward knockback and hit-spark cue, but affected melee clones and Skeleton summons must also be staggered for about 760 ms: pause their swarm movement and attacks during the stagger, show brief hit feedback, then let them resume swarming and attacking. Their knockback displacement should remain compact and decay quickly. Ranged clones keep their existing behavior and are not given the melee stagger; their outer formation mentality is unchanged.
- Warriors should visibly travel from the machine area toward the boss before attacking, rather than simply appearing in a battle formation.
- When approaching combat formation, clones must route around the boss perimeter instead of crossing through its sprite. They first reach a safe orbit radius, move tangentially around the boss to their assigned angular slot, then move outward only for ranged units; maintain a minimum center-to-center clearance from the boss while crowding it. The radial approach direction must always move an outside clone inward toward the safe orbit (and an inside clone outward); new and restored clones should begin at the machine's room-side exit point, not inside the machine or beyond the room boundary. Orbit-angle calculations must use the clone's position relative to the boss (not the reverse vector), and movement bounds must match the full 320-pixel room width so the right-hand formation slots remain reachable.
- Warriors need readable idle/movement/attack/defeat states as supported by the chosen art assets.
- The boss has health and a clear defeat state.
- The boss should react to incoming attacks where practical.
- Boss death is a distinct sequence; rewards and the next boss follow that sequence.
- The game should communicate progress even when many warriors are present. Avoid visual effects that make the boss, warriors, or room unreadable.

## Idle and incremental expectations

The game should reward both active interaction and letting the simulation run.

- Production and combat should proceed automatically after upgrades are purchased.
- The army starts with a capacity of 26 active clones. The repeatable Clone Capacity upgrade adds 5 slots per purchase, and the HUD displays active clones / current capacity rather than lifetime clones produced.
- When active clones plus queued respawns fall below the upgraded capacity, automatic production fills only unreserved slots according to the current batch size and production rate. Pending respawns reserve their own slots until they return, preventing overproduction and stuck replacement queues.
- Clone Capacity costs 250 credits initially and scales by 1.8× per purchase; its level is stored in the local save.
- Progression should be incremental and understandable: the player can see how each machine upgrade improves output or unlocks new options.
- Large numeric counters use compact suffixes consistently: thousands `k`, millions `M`, billions `B`, and trillions `T` (for example, 10,000 displays as 10k). Values below 1,000 remain whole numbers.
- Save player progress locally in the browser so a refresh does not erase the run.
- Use elapsed-time/offline progress only when it can be implemented reliably and capped sensibly; never grant duplicate or implausible rewards after clock changes or long absences.
- Keep core game state separate from UI rendering so balancing and saving remain reliable.

## Mobile-first interaction requirements

- Portrait iPhone Safari is the primary target.
- The entire lab play area and its interactive machine must fit within the viewport without page scrolling. The upgrade sheet may scroll internally when its contents exceed the available height.
- Interactive targets, especially the cloning machine and upgrade controls, must be comfortable to tap.
- Upgrade panels should scroll internally when needed; avoid making the entire game screen unexpectedly scroll.
- Respect iPhone safe areas and browser viewport changes.
- Keep text legible at phone size and avoid relying on hover interactions.
- Desktop layouts may use additional space but must preserve the same visual hierarchy and game rules.

## Startup and asset initialization

- On every page load, show a dedicated branded loading screen before the title menu.
- The loading screen must report real initialization stages and must not expose PLAY until required laboratory, warrior, boss, and pixel-font assets have finished loading.
- Optional UI and particle-effect assets may fail without blocking startup; required scene and character assets must fail visibly and offer a retry instead of allowing a partially initialized game to start.
- After successful initialization, reveal the title screen with PLAY and RESET SAVE. Restore the local save only after the player chooses PLAY.
- Keep the simulation paused behind the startup screens; loading and title presentation must not advance production or combat.

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

## Clone approach and formation behavior

- Newly produced and restored clones begin at the cloning machine output and use a deliberate route to the boss: (1) walk radially inward to the shared inner perimeter, then (2) travel around that perimeter to their deterministic assigned formation angle. Ranged units then move outward to their assigned firing radius.
- Knights and Skeleton summons use the compact inner ring only as their gathering formation. Once the currently deployed melee group has reached its assigned angles, it transitions into a dense, fast bee-like swarm pressed tightly against the boss perimeter. They retain circular movement but periodically surge inward together, creating a mob-like rush at the boss. Vary angular speeds and phases between units, while keeping radial distance tightly constrained to roughly 9–15 room pixels beyond the boss radius and maintaining a small sprite-clearance margin. They must not hold a wide orbit or scatter across the room.
- Mages, Archers, and Necromancers keep the same angular slot pattern at the wider ranged radius. Once they reach their assigned outer slots, they hold position and attack; do not apply the melee swarm behavior to them.
- If the roster changes and a clone's assigned angle changes, it reconverges through the same perimeter approach/orbit sequence before resuming its class-specific behavior.
- Keep crowd separation as a small local anti-overlap nudge only; it must not redirect clones away from their assigned formation path.


## Necromancer and summoned skeletons

- The Elder hero is the **Necromancer** clone class and is part of the random DNA Research discovery pool. Once discovered, Necromancers can be produced by the cloning machine and are restored through the existing clone-save roster.
- Necromancers are ranged units: they use their own four-direction Elder idle and walk strips, hold the same outer ranged formation radius as Mages and Archers, and fire the existing arcane projectile toward the boss. The pack does not include a dedicated Elder attack strip, so the idle pose is used while the arcane cast/projectile effect communicates the attack.
- While at least one Necromancer is active, the army maintains up to one temporary Skeleton summon per two active regular clones. Summoning is paced at one Skeleton every 2.2 seconds until the target count is reached. Summons do not consume clone capacity, enter the production pool, count toward the clone HUD, or recursively increase their own summon target.
- Each Skeleton uses the imported four-direction idle/walk strips and the pack's hit/death strips. It appears beside its Necromancer, routes to an assigned slot on the shared inner melee formation ring, and attacks the boss with a melee strike. Skeletons have 70% of the current base clone health (rounded down, minimum 1 HP) and deal 65% of normal clone damage.
- Boss attacks can damage summons. When a Skeleton's health reaches zero it plays its death animation and is removed; an active Necromancer can summon a replacement while the army remains above the one-per-two target. Summons are temporary battle entities and are intentionally not persisted in the saved clone roster.


## Skeleton ground-rise summoning effect

- Each Skeleton begins in a short 850 ms summoning state at the Necromancer's position before it starts moving into its melee formation slot. It cannot move or attack while emerging.
- The actual imported Skeleton idle sprite is revealed upward from below the floor with a crisp clipped rise, a dark ground opening, fine cracks, and small pixel soil/violet motes. The existing arcane portal and magic-circle effects provide a restrained magical accent. The effect is cosmetic and does not change summon count, health, or combat balance.


### Skeleton visual readability

- Summoned Skeletons have a compact pulsing cyan/violet ground aura and cyan silhouette glow so they remain identifiable among large clone crowds. The aura follows their position and animation; it does not recolour the source sprite or affect combat behavior.


### Necromancer deployment and summon feedback

- The first successful Necromancer DNA discovery immediately deploys an Elder clone when capacity permits, in addition to unlocking it in the production pool. Existing saves with Necromancer DNA but no active Elder or queued Elder replacement receive a queued recovery deployment.
- A persistent lab-room status strip below the boss health bar reports active Necromancers and Skeletons versus their current target, or clearly indicates locked DNA / pending recovery.
- Skeleton combat uses the imported named `hit` strip during attacks and the named `death` strip on defeat; these are resolved by their actual manifest names, not directional animation aliases.

### Burning countdown UI clarity
- The boss-side burning indicator retains the game’s `Pixels` font for both the `BURNING` label and seconds countdown. Keep it compact so it occupies less of the play area (98 × 56 room pixels) while remaining easy to read through bold pixel lettering, a high-contrast dark backing, a dark text outline, clear spacing, and a wide progress bar relative to the panel. Do not switch to a sans-serif font. Burn damage and duration remain unchanged.
