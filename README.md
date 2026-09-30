> **This is the sprite-experiment copy**, branched off the main project to
> test single-sheet sprite rendering without risking the base build. It uses
> **direct texture stream loading** (`File.OpenRead` + `Texture2D.FromStream`)
> for `Content/All free tiles.png` rather than the Content Pipeline, so there is no
> `Content.mgcb` or `dotnet-mgcb` tool installation required.
>
> **Sprite Rendering:** Instead of multiple individual image files or colored
> placeholder rectangles, all tiles and entities are sliced at runtime from
> `Content/All free tiles.png` (a 16x16 grid-based tileset) using standard
> `sourceRectangle` parameter coordinates in `_spriteBatch.Draw()`. Coordinates are
> neatly mapped inside `TileSprites.cs`.
# TileQuest — Forest Village Defense
A 2D grid-based action RPG built in MonoGame (C#) for a Data Structures &
Algorithms (DSA) course project. Set across a 5-night story arc, the player awakens
in a quiet forest village, gathers resources, crafts gear, and defends the central
Village Hearth from escalating nightly monster waves — leading up to a confrontation
with a traitorous Village Elder and a final assault on the forest lair.
---
## Story & Narrative Progression (5-Night Arc)
- **Day 1 / Night 1 — Arrival & First Attack:** Wake up in the village after getting lost. Kind villagers take you in; you repay them by defending the Village Hearth during the initial monster raid.
- **Day 2 / Night 2 — Investigation & Forest Patrol:** Venture into the surrounding forest to gather wood/stone, scout monster spawn points, and clear out stray forest beasts.
- **Day 3 / Night 3 — The Monster Hideout:** Discover the monsters' forest lair. Fight through an intense wave, but realize your current gear is insufficient and fall back to the village.
- **Day 4 / Night 4 — The Traitorous Elder:** Uncover secret documents revealing the Village Elder has been orchestrating the attacks to keep the villagers dependent on his power. Defeat the Elder in a 1-on-1 boss battle in the village square to unlock his **Arcane Burst** skill.
- **Day 5 / Night 5 — The Final Stand:** Launch a final assault against the monster horde and lair using your newly acquired Arcane Burst skill to determine the fate of the village.
---
## Endings & Game State Machine
The game features three distinct endings based on player actions and survival:
1. **Ending A — True Victory (Hero of the Forest):** Defeat the final boss wave on Night 5. The village is saved, and your final score is recorded on the leaderboard.
2. **Ending B — Defeat (Fall of the Hearth):** The Village Hearth's health drops to 0 during any night phase.
3. **Ending C — Secret Ending (The Deserter):** Choose to step onto the `ForestExit` boundary tile during Day 4 or Day 5 and abandon the village to save yourself.
---
## Required DSA Topics (Grading Checklist)

| # | Topic | File(s) | Status | Game Implementation |
| :--- | :--- | :--- | :--- | :--- |
| 1 | **Queue** — Wave Spawner | `EnemySpawnInfo.cs`, `WaveSpawner.cs` | ✅ Built | FIFO queue managing nightly enemy spawn order & Elder's summoned adds |
| 2 | **Stack** — Undo System | `PlayerAction.cs`, `ActionHistory.cs` | ✅ Built | LIFO stack to reverse/undo crafting and defense placement during the Day phase |
| 3 | **LinkedList** — Inventory | `Item.cs`, `Inventory.cs` | ✅ Built | Dynamic insertion and removal of collected resources and equipment nodes |
| 4 | **Binary Search** — Shop / Recipes | `BinarySearchUtil.cs`, `CraftingRecipe.cs` | ✅ Built | $O(\log n)$ lookup for items and crafting costs at the Village Trader |
| 5 | **Insertion Sort** — Inventory / Scores | `InsertionSortUtil.cs` | ✅ Built | Auto-sorting inventory items and ranking final game scores on the leaderboard |

---
## Project Phases (Expanded Development Roadmap)

| Phase | Scope & Feature Focus | Status |
| :--- | :--- | :--- |
| **Phase 1** | Engine foundation, grid movement, `All free tiles.png` sprite sheet mapping, and isolated DSA modules | 🟡 In Progress |
| **Phase 2** | Fixed Village/Forest map layout, Day/Night `TimeSystem`, and `VillageHearth` state | Not Started |
| **Phase 3** | Resource harvesting (wood/stone) & `LinkedList` inventory integration | Not Started |
| **Phase 4** | Barricade crafting & `Stack<Action>` Undo building system | Not Started |
| **Phase 5** | `Queue` wave spawner integration (Nights 1–3), melee combat, & Hearth HP tracking | Not Started |
| **Phase 6** | **Night 4 Traitorous Elder Boss fight** & unlocking the **Arcane Burst** spell | Not Started |
| **Phase 7** | Village Trader shop (`BinarySearch`), Night 5 Lair Finale, & 3 Narrative Endings | Not Started |
| **Phase 8** | High score leaderboard (`InsertionSort`), HUD polish, & final presentation cleanup | Not Started |

---
## Building & Running
**Prerequisites:** .NET SDK (8.0 or later).
```bash
# Restore dependencies and launch the game
dotnet restore
dotnet run