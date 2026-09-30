# Better Run Logs Replayer

> **Status: not built yet.** This README describes the planned tool. Nothing here works yet.

Replays a run recorded by [Better Run Logs](https://github.com/cmyers009/better-run-logs) inside the real game. It starts the
same seed and character and applies every recorded decision in order. After each step it checks
that the game's RNG streams and state match the log.

Use it to:

- **watch** a streamer's run back move by move
- **verify** a log: the replay stops at the first step where the game and the log disagree, and
  says what differed
- **jump** to any floor or turn of a run to study a decision

## Install

1. Install Slay the Spire, **ModTheSpire** and **BaseMod** as described in the
   [Better Run Logs install steps](https://github.com/cmyers009/better-run-logs#install).
2. Download `better-run-logs-replayer.jar` and put it in the game's `mods` folder.
3. Launch with **Play With Mods** and tick **BaseMod** and **Better Run Logs Replayer**.

You don't need Better Run Logs installed to replay a log, only to record one.

## Getting a log to replay

A log comes from the game folder of whoever recorded the run:

```
<game folder>/better-run-logs/<CHARACTER>/<timestamp>.jsonl.gz
```

For example, on Windows:

```
C:\Program Files (x86)\Steam\steamapps\common\SlayTheSpire\better-run-logs\IRONCLAD\1790807044.jsonl.gz
```

The [Better Run Logs README](https://github.com/cmyers009/better-run-logs#finding-your-game-folder) lists the game folder
for Windows, Linux (native, Flatpak, Snap), Steam Deck and macOS. The quickest route on any system
is Steam → right-click Slay the Spire → **Manage** → **Browse local files**.

Copy the `.jsonl.gz` file into your own game folder under:

```
<game folder>/better-run-logs-replayer/
```

## Replaying

From the main menu, open **Replay** and pick a log. Controls:

| Key | Action |
|---|---|
| Space | play / pause |
| → | step one action |
| Shift + → | skip to the next turn |
| Page Down | skip to the next floor |

If the replay diverges, it pauses and writes a report next to the log,
`<timestamp>.divergence.txt`, naming the step, the RNG stream or value that differed, and both
values.

## Requirements for an exact replay

- The same game version the log was recorded on (`version` in the log's first line)
- The same set of gameplay-affecting mods (the log records the mod list)
- A log that ends in a finished run, or you accept that it stops where the log stops
