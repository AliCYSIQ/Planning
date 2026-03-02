# Deep Analysis

## What The Other AI Got Right

- One project per video → correct structure
- Projects mostly match what's taught
- The "compare to Unity's built-in" idea is excellent for catching bugs
- Using Gizmos for visual debugging → genuinely useful

## What's Wrong or Off

**Per-video mismatches:**

- **Video 4** (Freya - "Why can't you multiply vectors?") → He gives you an aim-assist + barycentric project. That video is actually about _why quaternions exist algebraically_, not barycentric coordinates. The project teaches wrong things.
- **Video 2** (Jorge Rodriguez) → The "clip space inspector" is over-engineered. Jorge's series is about applying vectors to game features, not building a rendering pipeline.
- **Video 3** (Quaternions 3B1B) → asking you to implement matrix→quaternion conversion is advanced and not what the video covers. The video gives _intuition_, not derivation.

**The two big projects (Mid + Final) are severely over-engineered:**

- "Mini Game Engine with BVH, dual quaternion skinning, modular packages, NUnit tests" → that's 6+ months of senior work, not a mid-level learning project
- Mid project is fine in concept but has too many systems at once

---

# ✅ My Final Version — Detailed

---

## 📦 After Video 1 — _Essence of Linear Algebra_ (3Blue1Brown)

**What the video teaches:** Vectors, dot product, cross product, matrix as transformation, determinants, basis change

**Project: Vector Math Visualizer**

Build a Unity scene with NO Unity Vector3/Mathf in your math code. Use only your classes.

**Build exactly this:**

- `MyVec3` class: add, subtract, scale, dot, cross, magnitude, normalize
- `MyMat4` class: multiply matrix × vector, multiply matrix × matrix
- Debug scene: 3 arrows showing X/Y/Z basis, one arrow showing a projected vector onto another

**What to see when done:**

- Place two arrows in the scene, press Play, see the projection of one onto the other drawn as a third arrow
- Change the angle between them and watch the projection update

**Acceptance test:** Your `MyVec3.Dot(a, b)` result matches `Vector3.Dot(a, b)` to 4 decimal places.

---

## 📦 After Video 2 — _Math for Game Developers_ (Jorge Rodriguez)

**What the video teaches:** Applying vectors/matrices to game problems — movement, angles, orientation, camera basics

**Project: Practical Vector Toolkit Demo**

3 small scripts in one scene, each solving a game problem with your math:

**Build exactly this:**

- **Script 1:** An enemy that knows if the player is in front or behind it → uses dot product of forward vector and direction to player
- **Script 2:** An object that always faces another object → uses cross product to find the rotation axis
- **Script 3:** A "is target in FOV" check → dot product + angle threshold, draws a cone in Gizmos

**What to see when done:**

- Sphere turns green when player enters the enemy's FOV cone, red when outside
- Gizmos show the actual math (direction vectors, projection lines)

**Acceptance test:** FOV check works correctly at all player positions. No use of Unity's `Vector3.Angle` or `Vector3.Dot` — only yours.

---

## 📦 After Video 3 — _Quaternions and 3D Rotation_ (3Blue1Brown)

**What the video teaches:** What quaternions _represent_, why they work for 3D rotation, intuition for the double-cover

**Project: Rotation Comparison Demo**

**Build exactly this:**

- `MyQuaternion` class: multiply, normalize, to/from axis-angle, SLERP
- Scene with two objects: one rotates using Euler, one using your quaternion SLERP
- A third object that rotates 90° on X, then 90° on Y — test with Euler vs quaternion

**What to see when done:**

- Euler object hits gimbal lock (rotation breaks or snaps) at certain angles
- Quaternion object interpolates cleanly every time
- SLERP gives constant angular speed, lerp does not

**Acceptance test:** SLERP between two opposite rotations doesn't flip or snap. Euler version does.

---

## 📦 After Video 4 — _Why can't you multiply vectors?_ (Freya Holmér)

**What the video teaches:** Why algebraic multiplication of vectors doesn't work simply, geometric algebra intuition, why quaternions are the natural solution

**Project: Rotation Composition Chain**

This video is about understanding _why_ quaternions exist algebraically. Project matches that.

**Build exactly this:**

- 3 objects in a chain: Object A rotates, Object B rotates relative to A, Object C relative to B
- Implement this with your `MyQuaternion` multiplication (composition)
- Add a toggle: switch the same chain to Euler angles and observe what breaks

**What to see when done:**

- Quaternion chain stays smooth at all angles
- Euler chain shows issues when axes align
- You understand that quaternion multiplication = composing rotations, which is exactly what the video explains

**Acceptance test:** Rotating the chain 360° brings all objects back to exact starting orientation (no drift). Euler version drifts or breaks.

---

## 📦 After Video 5 — _Essence of Calculus_ first 6 videos (3Blue1Brown)

**What the video teaches:** Derivative as rate of change, integral as accumulation, how velocity/acceleration/position relate

**Project: Physics Integrator Comparison**

**Build exactly this:**

- A ball falling under gravity. Implement 2 integrators:
    - Explicit Euler: `velocity += gravity * dt`, `position += velocity * dt`
    - Semi-implicit Euler: `velocity += gravity * dt`, `position += velocity * dt` (velocity updated first)
- A UI graph that draws position over time for both
- A `dt` slider (0.01 to 0.1) to show instability

**What to see when done:**

- At large `dt`, explicit Euler ball flies off. Semi-implicit stays stable.
- Graph shows the difference visually
- You understand that integration is just accumulating small changes — exactly what calculus videos teach

**Acceptance test:** At `dt = 0.05`, explicit Euler ball clearly diverges. Semi-implicit stays grounded.

---

## 📦 After Video 6 — _The Continuity of Splines_ (Freya Holmér)

**What the video teaches:** Bezier curves, Hermite curves, C0/C1/C2 continuity, why splines are designed the way they are

**Project: Spline Path Editor + Follower**

**Build exactly this:**

- A simple custom editor: click to place 4 control points, draw the Bezier curve between them using `OnDrawGizmos`
- Connect multiple curve segments with C1 continuity (tangent matching)
- An object that follows the full path at constant speed (arc-length reparameterization — pre-sample the curve, measure distances, move by distance not by t)

**What to see when done:**

- Drag control points → curve updates live in scene view
- Object moves at constant speed regardless of control point spacing
- Break C1 continuity intentionally and see the visible corner

**Acceptance test:** Object takes the same time to travel any equal-distance section of the spline. Moving control points doesn't change travel speed.

---

## 📦 After Video 7 — _Lerp smoothing is broken_ (Freya Holmér)

**What the video teaches:** Why `Lerp(a, b, 0.1f)` every frame is framerate-dependent, exponential decay as the correct approach, critically damped spring

**Project: Camera Follow System — 3 modes**

**Build exactly this:**

- A camera following a moving target with 3 switchable modes:
    - **Broken Lerp:** `pos = Lerp(pos, target, 0.1f)` each frame — show it's framerate dependent
    - **Fixed Lerp:** framerate-independent version using `1 - Mathf.Pow(decay, dt)`
    - **Spring:** critically damped spring that follows with velocity
- A `timescale` slider (0.5x to 2x) to expose the framerate dependency

**What to see when done:**

- At 0.5x timescale, broken lerp camera lags more than at 2x timescale
- Fixed lerp and spring behave identically regardless of timescale
- Spring version has natural feel — slight overshoot configurable

**Acceptance test:** Fixed lerp reaches 99% of target in the same real-world time regardless of timescale setting.

---

## 📦 After Video 8 — _Coding Adventures_ (Sebastian Lague)

**What the video teaches:** Applied math in real systems — just pick 1-2 episodes that interest you

**Project: Reproduce One Thing From Scratch**

Pick ONE of these (whichever Lague episode you watched):

- Procedural terrain with noise → implement 2D Perlin noise, generate a mesh
- Simple pathfinding → A* on a grid using vector math for heuristics
- Marching cubes → iso-surface extraction

**Rule:** No tutorials outside of the Lague video. Build it yourself using math you already know.

**Acceptance test:** Your result looks recognizably like Lague's. You can explain every line.

---

# 🏗️ Mid Project — After Videos 1–5

**Name: Third-Person Character Demo**

One scene, one character, you wrote all the math.

**Build exactly this:**

1. Character moves in world space using your `MyVec3` — WASD moves relative to camera forward
2. Character rotates to face movement direction using `MyQuaternion.SLERP`
3. Camera follows using your fixed-lerp smooth follow (from Video 7 exercise, apply early)
4. A jump with gravity using your semi-implicit Euler integrator
5. FOV cone shows enemies detecting the player (Video 2 exercise integrated)

**What you DO NOT build:** inventory, combat, animations, UI, levels.

**Acceptance test:**

- Movement feels smooth at any framerate
- No gimbal lock at any camera angle
- Jump arc is consistent regardless of framerate (test with timescale slider)

---

# 🏆 Final Project — After All 8 Videos

**Name: Spline Racing Game (Minimal)**

A small but complete playable thing. One track, one vehicle, finish line.

**Build exactly this:**

1. A closed spline track (Video 6) — editor-placed, displayed in scene
2. A vehicle that follows the track but the player steers left/right offset from the spline path
3. Rotation using your `MyQuaternion` — vehicle banks into turns
4. Speed system using your integrator — accelerate, brake, constant-speed normalization
5. A second AI vehicle that follows the spline perfectly using arc-length param at fixed speed
6. Simple sphere collision between the two vehicles — they push each other

**What you DO NOT build:** multiple tracks, UI menus, particle effects, sound.

**Acceptance test:**

- You can race the AI and win or lose
- Vehicle rotation never gimbal locks
- Collision between vehicles is stable (no explosion/tunneling at normal speeds)
- Track editor works — you can reshape the track without changing code

---

## Summary of Changes From The Other AI

|Topic|Their Version|My Version|
|---|---|---|
|Video 4 project|Aim assist + barycentric (wrong topic)|Rotation composition chain (matches video)|
|Video 3 project|Matrix→quaternion conversion (too advanced)|Gimbal lock comparison (matches intuition video)|
|Video 2 project|Clip space inspector (over-engineered)|FOV + facing (matches Jorge's content)|
|Mid Project|Tactical Arena (too many systems)|Third-person demo (focused, achievable)|
|Final Project|Full mini engine + BVH + dual quaternions|Small racing game (complete, ships)|