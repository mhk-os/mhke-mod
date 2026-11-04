# mhke-mod

Moorhuhn Kart Extra as a mod for Moorhuhn Kart: Open Source Edition, with 10 tracks, karts, powerups and effects converted from Moorhuhn Kart and Moorhuhn Kart Extra. The game ships it preinstalled and builds it from this repository. Every push to main also publishes a GitHub release with a zip per platform that you can put into the Mods folder of the game to install a newer build.

Track proportions are corrected against the original games' road widths and lap lengths relative to kart size. Outdoor, Scribble Blocks, Kart Track, Moon and Docklands were enlarged ×1.495; Desert, Canyon, Ice, Volcano and Graveyard were reduced ×0.748 to remove the import's inconsistent scale groups. Item boxes retain their size and ground clearance; racing lines, collision, grids and track distances follow the corrected geometry, and lighting was rebaked. This changes lap times and invalidates old track ghosts.

## Fireball

The fireball floats above the road and spins upright like a kart, not end over end. Its local-X spin pivot is oriented upright, with the mesh counter-rotated to retain its neutral pose. The visual uses scale 0.40333334, twice the previous 0.20166667, without changing its flight or collision tuning. Its straight-line chase speed is 36.125 m/s, half the previous 72.25 m/s. The flight sound has a 2 m minimum distance and 60 m maximum distance.

It launches forwards even while looking backwards, then drives the main path and alternative routes toward the current race leader. For the first second it cannot target its launcher: if the launcher leads, it drives forwards without a target to create an escape gap. Other leaders are eligible immediately, including during that window. Once the window ends, the launcher can be targeted after the fireball has cleared its body. Steering projects onto the solved drivable line and advances the look-ahead in world metres, preventing orbiting where raw track distances bunch up at Luna's kinks. Route handovers follow the smoothed road geometry instead of waiting to cross raw path-node planes. Solid walls stop or deflect its movement without destroying it; other fireballs do not block it, and its lifetime remains 30 seconds.

Inside 4 m of the leader's rear chassis extent it eases toward 95% of that kart's normal, unboosted top speed. Standing off from the body keeps normal cruising safe, while a brief partial slowdown lets the fireball catch up. Ahead of the leader, it takes 0.2-second forward steps every 0.5 seconds instead of stopping completely. These longer steps creep at 3 m/s when far ahead and accelerate toward 85% of the leader's normal top speed as the gap closes inside 4 m, using the same swept road navigation and wall collision. This fixed-step timing adapts the original game's throttle/coast creep without its frame-rate dependence. Lap-aware progress distinguishes waiting from a finish-line crossing. A dead or respawn-protected leader does not stop its route traversal and cannot consume it.

Close pursuit gently weaves from side to side, with an aim offset up to 0.65 m and a 2.4-second period. This is physical, swept movement rather than an offset of the model: the road edges constrain it, and it fades out before contact so a brief slowdown still lets the fireball catch the leader. Waiting and dead/respawn-protected targets do not enable the weave.

Touching an eligible leader's chassis applies the boil and consumes the fireball in the same physics step, including stationary overlaps and swept passes. Locking on adds no further hit delay. Walls still block contact.

A hit boils the leader for 2.5 seconds: both kart and driver soften into a warm, rippling pool, with a translucent white-blue water sheen, white steam and water droplets. Both particle systems radiate outward from upward-facing cones, with extra world-up velocity carrying them higher without increasing sideways spread. Their velocity axes use matching TwoConstants modes, with X/Z kept at zero. Full deformation takes 0.708 seconds, twice as fast as the previous 1.417 seconds, without shortening the gameplay penalty. Other kart and driver animations pause while the deformation and particles continue. There is no spin-out or character death animation. The effect respawns the kart when it ends; deformation, water overlay, expanded renderer bounds, particles and animation pauses are cleared when it ends, is cancelled or the kart respawns.

Hits and lifetime expiry end in a detached burst of 440 large, soft steam particles, including hits confirmed online. The puffs grow, rise and fade rather than flying in watery arcs; they use the white steam material, zero gravity and translucent shading. The nonlooping burst destroys itself after playback. Walls still do not consume the fireball; scene cleanup and server-rejected uses stay silent.

## Audio

Music (including menu/title/highscore cues) is normalized per song to -16 LUFS. Effects use one attenuation-only gain per source game, matching group medians to the quietest source while preserving intentional differences between cues; borrowed clips follow their source game's gain. Decoded peaks stay below 0 dBFS. Local cue gains and track music volumes are unchanged.

## License

MIT. Game assets belong to their respective owners. If there is a problem with any of them, message me and I will remove it.
