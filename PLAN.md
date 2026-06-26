# PLAN

Goal: turn the current Missile Command HTML5 build into a more faithful, stable arcade-style clone and remove the recent regression-prone changes.

Current repo state:
- Branch: main
- HEAD: v10 + GitHub Pages deployment
- Files: index.html, .github/workflows/pages.yml
- History shows the game evolved through v2-v10 in one file; we need to preserve the best gameplay ideas while stripping unstable/over-stylized behavior.

Approach:
1. Inspect the current game in a browser for runtime errors / playability issues.
2. Compare the current implementation against earlier commits (especially v9/v8/v4) to identify the best working baseline.
3. Rewrite the core game loop and presentation to match classic Missile Command more closely:
   - 3 missile silos, 6 cities, wave-based enemy rain
   - cleaner CRT + arcade color palette, not just bright green
   - more authentic missile / explosion timing, sound, and enemy behavior
   - safer state transitions and no lockups
4. Verify in-browser and with static checks.
5. Commit the recovery changes and keep the repo clean.

Current pass notes:
- Explosion gradients are clamped so the canvas no longer throws on late-frame draws.
- Sound is pushed closer to the arcade feel with a short launch chirp, noise-backed explosions, and tighter saucer/game-over cues.
- Grid intensity is reduced and wave pacing is slightly less frantic for a more authentic cadence.
