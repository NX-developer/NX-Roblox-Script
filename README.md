# NX Roblox Script

An open-source Roblox utility hub built with the Rayfield UI library. Game-specific tabs only appear when you are inside the matching game.

## Loadstring

```lua
loadstring(game:HttpGet("https://raw.githubusercontent.com/NX-developer/NX-Roblox-Script/main/NX-Roblox-Script.lua"))()
```

## Features

### Universal
- **Main:** God Mode (kill-brick resistant, auto-revive), God Position (sky lock), Anti-Void, Fly (camera-direction, PC + mobile), NoClip (optimized), Remove Waves, Anti-AFK
- **Movement:** WalkSpeed / JumpPower sliders + Anti-Reset locks, Infinite Air Jump, Auto Walk, Auto Jump, Bhop Combo, Auto Spin (with speed slider)
- **Visuals:** Player ESP, Fullbright, FOV slider, Upside-Down Camera, FPS Counter, Ping Indicator, KeyStrokes overlay (PC + mobile joystick), draggable HUD with reposition mode
- **Combat:** Aimbot (wall-check), Hitbox glow, Camera Lock
- **Teleport V2:** 5 independent saved slots, Click Teleport (PC key/right-click + mobile tap), live player teleport list
- **Misc:** Reset Character, Rejoin, Server Hop, Destroy Hub

### Game-Specific (auto-detected by PlaceId)
- **Murder Mystery 2:** Role ESP (Murderer red / Sheriff blue / Innocent gray) with per-round re-scan, Identify Murderer/Sheriff, Dropped Weapon ESP, Role Death Alerts, Auto Coin Collect (40 bag limit)
- **Speed Escape:** Auto Step Farm (real walking), Treadmill/Finish/Trophy/Checkpoint teleports, stage object scanner
- **Kick a Lucky Block:** Base/Block teleport, Auto Kick loop, Auto Income/Free Claim collect, Rebirth, Speed/Weight upgrades (x1/x3/x10), diagnostic scanners

## Platform
Works on PC and mobile. Tested with standard Roblox executors.

## License
Licensed under the **Apache License 2.0** — see [LICENSE](LICENSE).

## Credits
- **UI:** [Rayfield](https://github.com/SiriusSoftwareLtd/Rayfield) by Sirius Software (used under its license).
- **Kick a Lucky Block mechanics:** mapped with help from the open-source community (Gumanba — github.com/gumanba/Scripts, and "Sloppy GUI"). No code was copied; their public work helped understand the game structure.

---
Maintained by **NX-developer** (Novatex).
