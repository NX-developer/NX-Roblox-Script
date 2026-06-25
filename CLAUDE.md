# CLAUDE.md

Persistent context for working on this repository. Read this before making changes.

## What this is

NX Roblox Script — an open-source, multi-game utility hub for Roblox, written in Luau and built on the Rayfield UI library. It loads through a Roblox executor via `loadstring`. Universal tools work everywhere; game-specific tabs appear only when the player is inside a supported game.

- Main file: `NX-Roblox-Script.lua` (single file, whole hub lives here).
- UI: Rayfield (`Window:CreateWindow`, `CreateTab`, `CreateToggle`, `CreateButton`, `CreateDropdown`, `CreateInput`, `Rayfield:Notify`).
- Loader: `loadstring(game:HttpGet("https://raw.githubusercontent.com/NX-developer/NX-Roblox-Script/main/NX-Roblox-Script.lua"))()`

## Validate before every commit (IMPORTANT)

There is no build step. Lua syntax must be checked with a parser. Standard `luac5.4` does NOT understand Luau syntax, so strip the Luau-only tokens first, then parse:

```bash
cp NX-Roblox-Script.lua /tmp/check.lua
sed -i 's/\bcontinue\b//g; s/+=/=/g; s/-=/=/g; s/\*=/=/g' /tmp/check.lua
luac5.4 -p /tmp/check.lua    # must exit 0 with no output
```

A real syntax error (not a Luau false positive) shows up after stripping those tokens. The most common bug introduced here: using `...` inside an inner `pcall(function() ... end)` closure — varargs only work in the function that declared them, so capture `local args = {...}` first and `table.unpack(args)` inside the closure.

## Architecture / conventions

- Game tabs are gated near the top: a `*_PLACE_IDS` table plus a check. Grow a Garden also falls back to matching `game.Name` so it survives place-ID changes (`placeMatches`).
- Shared helpers live after the services block: `copyToClipboard`, `guiButton(...)`, `clickGuiButton(btn)` (uses `getconnections`/`firesignal`).
- Each game tab fires the game's REAL remotes/GUI buttons discovered via the in-script "Scan ... (Copy to Clipboard)" diagnostic buttons. Prefer real names over guessing.
- Diagnostics print full output to console AND copy it to the clipboard so it can be pasted back for wiring.

## Code style

- All code is in English. NO comments unless explicitly requested.
- Code must be complete — never abbreviated or elided.
- Notifications/labels are concise and English.

## Git

- GitHub user: `NX-developer`. Brand: NX Team / Novatex.
- Commit messages in English: short and descriptive for a specific fix, `Update` for a general change.
- Never commit secrets/tokens.

## Design boundaries (kept intentionally)

These are deliberate product decisions, not bugs to "fix":

- Single-player / self-progression automation is in scope (farming, idle loops, own-garden grow/collect/sell, movement, visuals, ESP, local cosmetics).
- NOT in scope: tools that automatically harm other real players in competitive PvP, automating stealing from other players' gardens, or bypassing a game's anti-cheat / a platform restriction (e.g. teleport error 773). Auto-collect explicitly skips any "Steal" prompt.
- Cosmetic spawns (accessories, shirts/pants, face, headless/legless) are client-side only — they must not replicate to the server. Note: animations DO replicate, so they are not "local only".

## Supported games (PlaceIds)

- MM2: 142823291
- Speed Escape: 95082159892680
- Kick a Lucky Block: 89469502395769
- Grow a Garden 1: 124977557560410, 126884695634066
- Grow a Garden 2: 77085202503540, 97598239454123
