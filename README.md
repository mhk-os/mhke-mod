# mhke-mod

Moorhuhn Kart Extra as a mod for Moorhuhn Kart: Open Source Edition, with 10 tracks, karts, powerups and effects converted from Moorhuhn Kart and Moorhuhn Kart Extra. The game ships it preinstalled and builds it from this repository. Every push to main also publishes a GitHub release with a zip per platform that you can put into the Mods folder of the game to install a newer build.

Track proportions are corrected against the original games' road widths and lap lengths relative to kart size. Outdoor, Scribble Blocks, Kart Track, Moon and Docklands were enlarged ×1.495; Desert, Canyon, Ice, Volcano and Graveyard were reduced ×0.748 to remove the import's inconsistent scale groups. Item boxes retain their size and ground clearance; racing lines, collision, grids and track distances follow the corrected geometry, and lighting was rebaked. This changes lap times and invalidates old track ghosts.

## Audio

Music (including menu/title/highscore cues) is normalized per song to -16 LUFS. Effects use one attenuation-only gain per source game, matching group medians to the quietest source while preserving intentional differences between cues; borrowed clips follow their source game's gain. Decoded peaks stay below 0 dBFS. Local cue gains and track music volumes are unchanged.

## License

MIT. Game assets belong to their respective owners. If there is a problem with any of them, message me and I will remove it.
