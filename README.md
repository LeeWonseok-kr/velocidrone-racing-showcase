# VelociDrone Racing Lab

A personal project to fly racing drones autonomously in VelociDrone, verify valid race completions, and progressively reduce race times.

The project brings together a virtual controller, calibration, flight logging, state-feedback control, and a live dashboard. This repository contains a demonstration video and a high-level implementation overview. The executable controller and models are not distributed.

## Demonstration

[![Autonomous flight demonstration](preview.jpg)](https://github.com/LeeWonseok-kr/velocidrone-racing-showcase/releases/tag/demo-67.873)

**[Watch or download the 67.873-second race](https://github.com/LeeWonseok-kr/velocidrone-racing-showcase/releases/download/demo-67.873/demo-67.873s-sticks.mp4)**

The video shows actual simulator footage alongside dashboard snapshots recorded during the flight. Playback speed is unchanged, and no flight motion was generated. Stick movements and race status remain visible; only detailed tuning information is masked. The final still shows the official result of this race. Movement after the finish is separate from the timed race.

## Verified results

| Item | Result |
|---|---|
| Course | 2023 AU NATS 5inch |
| Race | 3 laps |
| Official total time | **67.873 s** |
| Holeshot | 2.584 s |
| Individual laps | 22.035 / 21.627 / 21.627 s |
| Progress | Earlier verified result: 141.063 s → 67.873 s |

Verification combined the official game result, ordered gate crossings, crash and damage indicators, original state logs, and selected frames. Detection of every contact is not guaranteed. Repeated success rates for each configuration and performance on other courses have not yet been established. The goal is the fastest leaderboard time; this demonstration is a step toward that goal.

## How it works

1. **Record:** Capture reference flights and simulator state, then align their timestamps.
2. **Control:** Calculate virtual controller inputs from the difference between the target flight path and the current position, velocity, and attitude.
3. **Verify:** Monitor gate progression and race status. A detected collision marks the attempt as a failure and triggers a restart from the starting position.
4. **Improve:** Analyze successful runs and failure segments to refine the flight path and speed through each section.

Machine learning models have also been trained and evaluated experimentally. However, **the run shown here was completed by a controller using a reference path and state feedback**. It does not demonstrate a vision-only neural controller or generalization to unseen maps. The system has not been applied to a physical aircraft.

## Repository scope

This is a portfolio repository. It does not include source code, model weights, raw stick or state datasets, detailed control equations or parameters, executables, or reproduction instructions. It is separate from the private development repository.

See [NOTICE.md](NOTICE.md) for usage terms. Rights to VelociDrone and in-game assets belong to their respective owners. This is an unofficial personal project.
