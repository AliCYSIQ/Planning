# GRAP THE FIGHT — Full Game Design Document

---

## Overview

**Game Name:** Grap the Fight  
**Engine:** Unity 6+  
**Render Pipeline:** URP (Universal Render Pipeline)  
**Genre:** First Person Action Shooter with Wave-Based Combat  
**Development Time:** 3 Months  
**Developer Level:** Intermediate Unity (still learning, not beginner)

---

## Core Fantasy

You are a bounty hunter armed with a single hybrid weapon — one side is a grappling hook, the other is a gun, and the entire weapon is infused with magic. You fight through arenas, clearing waves of enemies to earn bounty, upgrade your weapon, and push deeper into harder arenas. Movement is not just travel — movement is a weapon. You are never supposed to stand still.

The feeling the game should always give the player: **fast, aggressive, powerful, and always in control even when outnumbered.**

---

## What Makes This Game Special

The key philosophy borrowed from studying Ultrakill: **never give the player time to be bored.** From the moment a wave ends to the moment the next one begins, the transition should be fast. Between arenas, fast. Death screen, fast. The game never slows down or makes the player wait. This is one of the most important design decisions in the entire game.

---

## The Game Loop (Three Layers)

### Layer 1 — Moment to Moment (Combat Loop)

This is what the player is doing every second. Grappling around the arena constantly, never standing still, shooting enemies mid-swing, using magic to control the battlefield. The grapple hook is not just a traversal tool — it can pull enemies toward you, which creates a rhythm of: grapple to enemy → pull them in → blast them mid-air. This should feel incredible when it clicks.

### Layer 2 — Wave Loop

Survive a wave → enemies drop bounty currency → between waves a small shop appears with three random upgrade choices → player picks one → next wave starts immediately, harder, with new enemy types mixed in. This loop rewards survival and skill with meaningful choices.

### Layer 3 — Session Loop (Progression)

Clear enough waves in an arena to unlock the next arena. Each arena ends with a boss wave. Beat the boss, move to the next arena. Three arenas = one full session. This gives the player a sense of journey and escalation within a single play session.

---

## The Weapon — Heart of the Game

The weapon has three modes and the player switches between them fluidly mid-combat.

### Grapple Side

- Fires a hook that either pulls the player toward a surface or pulls an enemy toward the player.
- Pulling an enemy toward you and then blasting them mid-air is one of the core satisfying mechanics.
- Has a cooldown — short enough to feel fluid, long enough to require thought.
- Visual: a visible line or cable between the weapon and the target.
- Sound: weighty, impactful — not a thin zip sound.

### Gun Side

- Main damage dealer. Simple, punchy, satisfying.
- Ammo is limited — forces the player to think about shots rather than spray.
- Ammo can be refilled by picking up drops from dead enemies.
- Hit feedback is critical: hit stop (tiny freeze frame on bullet impact), screen shake on big moments, enemy knockback on death.

### Magic Side

- Magic charges as the player moves and grapples. The more aggressive the movement, the faster it charges. This directly rewards skilled, mobile play.
- The player picks one magic type at the start of each run (or arena depending on final design).
- Magic type options (at minimum, choose three to implement):
    - **Shockwave Blast** — a radial burst that knocks back all nearby enemies.
    - **Slow Field** — a temporary zone that slows all enemies inside it.
    - **Shield Burst** — absorbs one hit and then releases that energy back as a damaging pulse.
    - **Chain Lightning** — arcs between nearby enemies dealing damage to all.

---

## Enemy Design — Keep It Simple but Varied

Only five enemy types are needed to create interesting, varied waves. The complexity comes from mixing them, not from having many types.

### 1. Grunt

Basic enemy. Walks toward the player and shoots. Teaches the player the core loop. Should be easy alone, dangerous in groups.

### 2. Rusher

Sprints directly at the player with melee. Forces the player to use the grapple to reposition or to pull them in and blast. Does not shoot.

### 3. Shielder

Holds a large shield that blocks all bullets from the front. The grappling hook can yank the shield off, leaving them exposed. This forces the player to engage creatively rather than just shooting.

### 4. Floater

Hovers out of normal reach. Forces the player to use the grapple hook to reach them or to aim upward. Punishes players who forget about vertical space.

### 5. Heavy

Slow, tanky, hits extremely hard if it reaches the player. Requires sustained focus to kill. Creates pressure when mixed with Rushers that demand immediate attention.

### Wave Design Philosophy

Interesting waves come from combining enemy types that force conflicting priorities. Example: Rushers forcing close range attention while Floaters attack from above while a Shielder blocks bullets. The player has to prioritize, reposition, and use all three weapon modes.

---

## Arena Design — Three Arenas for a Three Month Build

### Arena 1 — The Yard (Tutorial Arena)

Open, flat, simple geometry. Teaches movement and basic combat. No verticality, no complexity. Introduces Grunts and Rushers. The player learns the core loop here. Visual theme: abandoned industrial courtyard.

### Arena 2 — The Stacks (Vertical Arena)

Multiple platforms at different heights. Forces grapple usage constantly. Introduces Floaters who specifically exploit the vertical space. Players who ignore the grapple will struggle here. Visual theme: collapsed warehouse interior with broken catwalks.

### Arena 3 — The Cage (Tight Arena)

Claustrophobic, narrow corridors, tight spaces. Makes magic much more important because enemies cluster. Floaters cannot be avoided. Shielders and Heavies are very dangerous in small corridors. Visual theme: underground prison or bunker.

---

## Boss Design — One Boss Per Arena

Each boss combines the mechanics of the enemies in its arena, plus one unique mechanic the player has never seen before.

### Boss 1 — The Warden (Arena 1 Boss)

A giant armored Grunt that spawns Rushers periodically. Unique mechanic: the player must grapple onto the Warden's back to attack a weak point. Teaches the player that the grapple hook works on bosses.

### Boss 2 — The Crane (Arena 2 Boss)

A Floater variant that is enormous and patrols between the platforms. Drops explosive projectiles. Unique mechanic: the boss has multiple weak points at different heights, the player must grapple between platforms rapidly to hit them all in sequence. Forces aggressive vertical movement.

### Boss 3 — The Brute (Arena 3 Boss)

A massive Heavy that also carries a shield and has a charge attack that destroys walls, changing the arena layout mid-fight. Unique mechanic: the player must use magic to stagger it before the shield can be pulled. Combines all systems: grapple, gun, magic, positioning.

### Mini Boss Concept (One Per Arena)

Each arena also has a mid-point mini boss that appears around wave 5 or 6. These are elite versions of regular enemies with one extra ability. They drop a guaranteed upgrade drop, making them a risk-reward moment.

---

## Progression System

### Between Waves — Shop

After each wave, a fast simple shop appears. Three random choices presented. Player picks one and the next wave starts immediately. Choices include:

- More ammo capacity
- Faster grapple cooldown
- Bonus magic charge rate from movement
- Temporary damage boost for next wave
- Health restoration
- Enemy slow effect on magic
- Bonus bounty from next wave (economic choice)

### Between Arenas — Permanent Loadout Choice

Between arenas the player chooses one permanent upgrade that carries through the rest of the session. These are more impactful than wave shop upgrades. Examples:

- Grapple pulls enemy toward player faster
- Magic damage increased permanently
- One extra magic charge allowed
- Gun fires two shots per trigger pull
- Grapple has a second charge (can grapple twice before cooldown)

### Roguelite Element

Each run the player starts fresh. Upgrades do not carry between runs. But with each run the player gets better mechanically. This keeps the game replayable and means a skilled player can clear it efficiently while a new player has to learn through repetition.

---

## Game Feel — The Most Important Section

These are small things but they are what separates a fun game from a flat one. Every single one matters.

- **Hit Stop:** A tiny freeze frame (2-4 frames) when a bullet connects with an enemy. This makes every shot feel like it has weight.
- **Screen Shake:** On explosions, boss slams, and magic use. Should be subtle on normal hits, dramatic on big moments.
- **Grapple Cable:** Must be visible and have a swing sound that feels weighty. The moment of impact when the hook lands should have a distinct audio cue.
- **Enemy Death Knockback:** Enemies should be knocked back visibly when killed. Not floaty — punchy.
- **Movement Speed:** The player should feel fast. Faster than they expect. This is what makes the game exciting.
- **No Dead Time:** Every transition — wave end to wave start, arena to arena, death to respawn — should be as fast as possible. Never make the player wait.
- **Magic Visual Feedback:** When magic is charging, there should be a visual indicator on the weapon or the player's hand. When it fires, it should be visually dramatic even if the effect is simple.

---

## Technical Decisions (Unity 6)

### Physics — Rigidbody (NOT Character Controller)

**This decision is final and important.** The grappling hook needs to pull the player through the air, build momentum, swing around, and carry that momentum when released. Character Controller cannot respond to physics forces — all of that would need to be faked manually, which is painful and never feels right. Rigidbody handles it naturally. The magic knockback, enemy physics, and explosive forces also all benefit from Rigidbody. The difficulty of Rigidbody is real but solvable and worth it.

### Input — New Input System

Use Unity's New Input System (not the old Input.GetAxis). Create an Input Action Asset. Set up Move, Look, Jump, Grapple, Shoot, and Magic actions. It feels different at first but it scales cleanly when adding more mechanics.

### Camera — Cinemachine 3

Use Cinemachine 3 (updated for Unity 6) for camera work, especially once the grapple swinging is implemented. It handles camera smoothing and offset naturally.

### Rendering — URP

Unity 6 made URP significantly more polished. Use it from the start, do not switch later.

---

## Player Controller Notes (What Was Solved)

During early development the following issues were identified and solved in the Rigidbody player controller:

**The Move Input Problem:** Input was only subscribing to `performed` but not `canceled`. When movement keys were released, the input vector never reset to zero. Fix: also subscribe to the `canceled` event on the Move action.

**World Space Movement Problem:** Movement direction was built from raw input with no relation to camera facing. Fix: build `_moveDirection` using `transform.forward` and `transform.right` instead of raw Vector3 axes.

**Jump Double Force Problem:** The jump was setting `verticalVel` to a launch value AND also firing a `ForceMode.Impulse` simultaneously. Both were pushing upward for many frames creating an enormous unintended jump. Fix: remove the Impulse entirely. Drive jumping purely through `verticalVel` which is already applied every FixedUpdate via direct velocity assignment.

**Grounded Reset Killing Jump:** `verticalVel` was being reset to -2f every FixedUpdate when grounded, including the same frame the player jumped. Fix: only reset when `isGrounded && verticalVel < 0`.

**Slow Jump Problem:** Using `ForceMode.Acceleration` to apply vertical movement meant velocity built up slowly over many frames. Fix: instead of AddForce for vertical movement, directly assign `rb.linearVelocity` with the Y component set to `verticalVel` every FixedUpdate. This makes the rigidbody move at exactly the intended speed immediately.

**Ground Check Radius:** Default radius of 5f was enormous causing player to always register as grounded even in the air. Fix: reduce to approximately 0.3f and ensure the `feetPoint` transform is positioned at the bottom of the character collider.

---

## Reference Games Studied

These games were studied during design. The goal is not to copy them but to understand what makes them great and adapt those principles.

- **Ultrakill** — Key takeaway: never give the player dead time. Fast level transitions, aggressive combat, movement as a weapon. Most important reference for this game.
- **Titanfall 2** — Key takeaway: how a grapple hook should feel in first person movement. Momentum, swing, and how the grapple flows into combat.
- **Doom Eternal** — Key takeaway: forced aggression in combat design. The player is always pressured to move and attack. Resource management mid-fight.
- **Hades** — Key takeaway: boss design and how bosses escalate. Fast death-to-retry loop.
- **Roboquest** — Key takeaway: roguelite FPS loop structure and upgrade system pacing.

---

## Three Month Development Roadmap

### Month 1 — Core Systems

- Week 1: Player controller (movement, jump, camera look) fully working and feeling good
- Week 2: Grapple hook mechanic — pulls player to surfaces and pulls enemies toward player
- Week 3: Shooting system with ammo, hit detection, and basic game feel (hit stop, screen shake)
- Week 4: Magic system — charge mechanic and at least two magic types working

### Month 2 — Content

- Week 1: All five enemy types implemented with basic AI
- Week 2: Wave spawner system, bounty drops, between-wave shop
- Week 3: Arena 1 and Arena 2 built with their mini bosses
- Week 4: Boss 1 and Boss 2 fully implemented

### Month 3 — Completion and Polish

- Week 1: Arena 3 and Boss 3 built and implemented
- Week 2: Full progression system, all upgrades, roguelite run structure
- Week 3: Audio, VFX polish, game feel refinement
- Week 4: Bug fixing, balancing, playtesting, final build

---

## Open Questions (To Be Decided After Playing Reference Games)

The following design questions were intentionally left open. The developer planned to play reference games (especially Titanfall 2 and Doom Eternal) before finalizing these decisions:

- What tone and visual style does the game use? (dark and gritty, fast and stylish, arcadey, atmospheric)
- What is the world setting? (sci-fi, dark fantasy, post-apocalyptic, mixed)
- How does the magic feel visually and thematically? (ancient magic, superpower, corrupted energy, elemental)
- What kind of overall progression structure? (pure roguelite, permanent upgrades, or both combined)
- How many magic types total?

These answers will shape the visual design, audio direction, enemy aesthetics, and some mechanics. Do not finalize art or audio direction until these are answered.

---

## Notes for Any Developer or AI Picking This Up

- The developer is intermediate level in Unity, not a beginner, but still actively learning.
- The game is built in Unity 6 using URP and the New Input System. Do not suggest solutions using legacy Input or HDRP.
- The Rigidbody choice over Character Controller is intentional and final — do not suggest switching.
- The developer prefers to understand the reasoning behind solutions, not just receive code. Explain the why before the how.
- When giving code, keep it clean, commented, and avoid over-engineering. One system at a time.
- The most important feeling to preserve in all design decisions: the game should never feel slow, and the player should always feel powerful and aggressive.