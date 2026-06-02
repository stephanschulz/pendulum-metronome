# Pendulum + Metronome — single-motor mechanism simulation

## Goal
3D simulation of a mechanism where ONE continuously-spinning motor drives:
- a **ground-mounted metronome** swinging **left↔right** (about Z axis)
- a **ceiling-mounted pendulum** swinging **forward↔back** (about X axis)
…and the two bobs cross the same central volume but **always miss each other**.

## Mechanism design (the engineering answer)
- Motor at the base → **flat belt** → a **vertical line-shaft** spinning continuously.
- Shaft carries **two eccentric crank pins** at different heights, **keyed 90° apart**.
- Each pin **winds a steel cable on/off** as it rotates, pulling its oscillator.
- 90° phase offset = quadrature: metronome angle ∝ sin(θ), pendulum angle ∝ sin(θ+90°)=cos(θ).
  - Both bobs can only collide if BOTH are at center at the same instant.
  - sin(θ)=0 AND cos(θ)=0 is impossible → guaranteed miss. This is the whole trick.

## Tasks
- [x] Scene scaffold: Three.js (CDN/importmap), orbit controls, floor, ceiling, lights.
- [x] Ground metronome (base + arm + bob), swings about Z.
- [x] Ceiling pendulum (mount + arm + bob), swings about X.
- [x] Vertical line-shaft + 2 eccentric crank pins (90° apart) + drums.
- [x] Motor + flat belt drive at the base.
- [x] Steel cables from crank pins to each oscillator arm (wind on/off look).
- [x] Drive kinematics: angleM = ampM·sin(θ), angleP = ampP·sin(θ+offset).
- [x] Live clearance readout + SAFE/COLLISION status + min-clearance tracker.
- [x] Controls: motor RPM, amplitudes, phase offset, pause, reset-min, camera.
- [x] HUD explaining the mechanism + a "set offset to 0° to see the crash" hint.

## Review
- Single file `index.html`, no build step. Open directly or `open index.html`.
- Phase offset is the key teaching control: 90° = always safe, 0° = collides.
