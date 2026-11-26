# Disable-Effect
Removes a desire skill effect so it will not clutter your screen only Projectile skills,Barriers,Shields  will stay visible
# Disable effect (V Rising, client-side)

A window (press **F9**) with one page per spell school. Each spell has a button to hide or show its effects.
**Projectile skills, barrier / shield skills, circle indicators and enemy effects (VBloods, NPCs) always stay visible.**
**F8** turns hiding on/off.

## Using it
1. Press **F9**. Pick a school on the left (Blood, Chaos, Unholy, Illusion, Frost, Storm), or *Barriers & Shields*, or *Other effects*.
2. Each line is a spell with its icon. Click its button: **SHOW** (green) turns into **HIDE** (red). A blue button means the spell is protected and
   cannot be hidden.
3. **Hide all / Show all** act on the page you are looking at (protected spells are skipped).
4. The top bar has the master switch (also F8) and the protections. The *Keys* buttons on the left change F8 / F9: click one, press the new key.
5. Scroll long lists with the mouse wheel or the bar on the right. Drag the title bar to move the window; **X** closes it. Your choices are saved.

Keyboard backup (works even if the mouse misbehaves): **Up/Down** select, **Left/Right** tick, **PageUp/PageDown** change page,
**Home** show all, **End** hide all, **Esc** close.

## What stays visible
- **Projectile skills** (from your list): Shadowbolt, Sanguine Coil, Carrion Swarm, Chaos Volley, Chaos Barrage, Corrupted Skull, Unholy Chains,
  Spectral Wolf, Wraith Spear, Curse, Crystal Lance, Frost Bat, Cyclone, Lightning Tendrils, Blood Storm, Serpent's Kiss, Wisp Dance.
  Any effect whose name contains *Projectile* inside a school is also kept. `ProjectileMode = PartOnly` keeps only that projectile part and lets
  you hide the spell's cast / hit effects.
- **Barriers and shields**: Chaos Barrier, Ward of the Damned, Frost Barrier, and generic `Part_Shield_*` effects (`KeepBarriers`).
- **Circle indicators**: effects drawn with the game's `AimPreview` shader (your log showed the indicator particles use it), the game's
  `HitCircleParticleComponent`, or names with Warning / Marker / Telegraph / Indicator (`KeepIndicators`).
- **Enemy effects**: anything under an object tagged `NPC`, or named VBlood / Boss / Enemy / Npc.
- **Spells you never cast** (`OnlyHideSpellsYouCast`, on by default): a ticked spell is hidden only after you have cast it yourself (seen right
  after your cast key or a click). So an enemy using a spell you never cast stays visible. The tag *cast by you* shows when that is known.

## Settings 
| setting | default | meaning |
|---|---|---|
| `General / Enabled` | true | master switch (F8) |
| `General / ToggleKey`, `MenuKey` | F8, F9 | change in the window or here |
| `General / EnableMenu` | true | allow the F9 window (false = run without it) |
| `General / ShowMessages` | true | short on-screen messages while the window is closed |
| `Protect / KeepIndicators` | true | circle indicators stay visible |
| `Protect / KeepProjectiles` | true | projectile skills stay visible |
| `Protect / KeepBarriers` | true | barrier / shield skills stay visible |
| `Protect / ProjectileMode` | All | `All` or `PartOnly` |
| `Protect / OnlyHideSpellsYouCast` | true | hide a ticked spell only after you cast it |
| `Protect / KeepPatterns` | Warning,Marker,Telegraph,Indicator | name words that mark an indicator |
| `Protect / KeepShaders` | AimPreview | shader name text that marks an indicator |
| `Protect / EnemyPatterns` | VBlood,Boss,Enemy,Npc | name words that mark an enemy effect |
| `Protect / ExcludePatterns` | UI,Canvas,Menu,Loading,Cursor | ignored completely |
| `Advanced / KeyDepth` | 1 | how effect names are built (1 = top meaningful name) |
| `Advanced / ActionKeys` | Q,E,R,C,T,Space,LeftShift | keys that count as "I just cast" (any mouse button counts) |
| `Advanced / ActionWindowSeconds` | 0.9 | how long after a cast new effects are credited to you |
| `Advanced / ScanIntervalSeconds` | 0.2 | how often effects are looked for (min 0.05) |
| `Advanced / LogDiscoveries` | false | log every new effect and how it was filed |
