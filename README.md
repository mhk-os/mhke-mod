# mhke-mod

Moorhuhn Kart Extra as a mod for Moorhuhn Kart: Open Source Edition, with 10 tracks, karts, powerups and effects converted from Moorhuhn Kart and Moorhuhn Kart Extra. The game ships it preinstalled and builds it from this repository. Every push to main also publishes a GitHub release with a zip per platform that you can put into the Mods folder of the game to install a newer build.

Track proportions are corrected against the original games' road widths and lap lengths relative to kart size. Outdoor, Scribble Blocks, Kart Track, Moon and Docklands were enlarged ×1.495; Desert, Canyon, Ice, Volcano and Graveyard were reduced ×0.748 to remove the import's inconsistent scale groups. Item boxes retain their size and ground clearance; racing lines, collision, grids and track distances follow the corrected geometry, and lighting was rebaked. This changes lap times and invalidates old track ghosts.

## Fireball

The fireball floats above the road and spins upright like a kart, not end over end. Its local-X spin pivot is oriented upright, with the mesh counter-rotated to retain its neutral pose. The visual uses scale 0.2016667: the previous 0.275 increased by 10%, then divided by 1.5. Its straight-line chase speed is 36.125 m/s, half the previous 72.25 m/s. The flight sound has a 2 m minimum distance and 60 m maximum distance.

It launches forwards even while looking backwards, then drives the main path and alternative routes toward the current race leader, including its owner after the initial two-second immunity. Steering projects onto the solved drivable line and advances the look-ahead in world metres, preventing orbiting where raw track distances bunch up at Luna's kinks. Route handovers follow the smoothed road geometry rather than waiting to cross raw path-node planes. Solid walls stop or deflect its movement without destroying it; other fireballs do not block it, and its lifetime remains 30 seconds.

Near the leader it eases toward 32.5% of that kart's normal, unboosted top speed. Both full chase speed and the close-pursuit reference are halved by the hotfix. A cruising leader can stay ahead, while braking lets the fireball catch up. An active leader behind it makes it wait; lap-aware progress distinguishes this from a finish-line crossing. A dead or respawn-protected leader does not stop its route traversal and cannot consume it.

A hit boils the leader for 2.5 seconds: both kart and driver soften into a warm, rippling pool, with a translucent white-blue water sheen, white steam and water droplets. Full deformation takes 1.417 seconds, 1.5 times faster than before, without shortening the gameplay penalty. Other kart and driver animations pause while the deformation and particles continue. There is no blast, spin-out or character death animation. The effect respawns the kart when it ends; deformation, water overlay, expanded renderer bounds, particles and animation pauses are cleared when it ends, is cancelled or the kart respawns.

## Audio

Music (including menu/title/highscore cues) is normalized per song to -16 LUFS. Effects use one attenuation-only gain per source game, matching group medians to the quietest source while preserving intentional differences between cues; borrowed clips follow their source game's gain. Decoded peaks stay below 0 dBFS. Local cue gains and track music volumes are unchanged.

## License

MIT. Game assets belong to their respective owners. If there is a problem with any of them, message me and I will remove it.
