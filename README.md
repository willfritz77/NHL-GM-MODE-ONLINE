# 🏒 NHL GM Mode

A browser-based NHL General Manager simulation game. No install, no server — just open the HTML file and play.

**[▶ Play it live](https://willfritz77.github.io/nhl-gm-mode/gm-mode.html)** ← update this link after enabling GitHub Pages

---

## What it does

- **All 32 NHL teams** with real rosters fetched live from the NHL API (`api-web.nhle.com`) when opened in a browser
- **Full GM tools** — roster management, trades, waivers, free agents, contracts, AHL farm
- **Season simulation** — sim week-by-week or skip to playoffs, with standings, injuries, and player stat accumulation
- **NHL Draft Lottery** — accurate weighted odds (18.5% down to 0.5%), two draws, max 10-spot jump rule
- **7-round draft** — AI teams draft by need, your picks go to your AHL roster
- **Offseason** — players age, ratings develop/decline, contracts tick down
- **Save/load** via browser localStorage

---

## How to run locally

Just download `gm-mode.html` and open it in any modern browser (Chrome, Firefox, Safari, Edge).

```
# Or clone and open:
git clone https://github.com/willfritz77/nhl-gm-mode.git
cd nhl-gm-mode
open gm-mode.html   # Mac
start gm-mode.html  # Windows
```

> **Note:** Live roster fetching from NHL.com requires running from a real browser (not the Claude artifact viewer), since the sandbox blocks external network requests. Hardcoded rosters from March 2026 are used as fallback.

---

## Project structure

Everything is in a single file intentionally — no build step, no dependencies, no node_modules. Just HTML + CSS + vanilla JS.

```
gm-mode.html          # The entire game
README.md             # This file
```

Key sections inside `gm-mode.html`:

| Section | What it does |
|---|---|
| `const TEAMS = {...}` | All 32 teams — colors, conference, division, AHL affiliate |
| `const ROSTERS = {...}` | Hardcoded fallback rosters (March 2026) |
| `DOMContentLoaded` | Fetches live rosters from NHL API on startup |
| `renderDash()` | War room dashboard |
| `renderRoster()` | Roster / contract management |
| `renderTrades()` | Trade builder |
| `renderWaivers()` | Waiver wire |
| `renderFA()` | Free agent signings |
| `renderStandings()` | League standings |
| `renderSim()` | Season simulation controls |
| `simWeeks()` | Core simulation engine |
| `simGame()` | Single game outcome engine |
| `runLottery()` | NHL draft lottery (real odds) |
| `renderDraft()` | 7-round interactive draft |
| `triggerEvent()` | Random GM events (injuries, trade demands, etc.) |

---

## Contributing

Pull requests welcome. Here are good areas to work on:

### Features needed
- [ ] **Contracts & extensions** — offer sheet system, RFA/UFA logic, cap holds
- [ ] **Trade AI** — smarter AI trade proposals based on team needs and cap space  
- [ ] **Player development** — prospect progression system in the AHL
- [ ] **Coaching staff** — hire/fire coaches, lines/system affect sim outcomes
- [ ] **Scouting** — hidden prospect ratings revealed by scouting budget
- [ ] **Multi-season tracking** — dynasty mode, historical records
- [ ] **Cap penalties / LTIR** — long-term IR cap relief mechanic
- [ ] **Trade picks** — pick trading in the trade builder
- [ ] **Injury detail** — specific injury types, surgery/recovery timelines
- [ ] **Mobile UI** — better touch support and responsive layout
- [ ] **Sound effects** — crowd noise, goal horn on big moments

### Known issues
- Roster fetch can fail in sandboxed environments (by design — works in real browsers)
- Schedule generation produces ~79 games per team instead of exactly 82
- Draft prospects are randomly generated — would be better with real prospect data
- Playoff bracket display could be more visual

### How to contribute

1. Fork the repo
2. Make your changes directly in `gm-mode.html`
3. Test by opening it in Chrome — open DevTools console to check for errors
4. Submit a pull request with a description of what you changed and why

No build process, no linting setup, no CI required. Just make sure the browser console is clean.

---

## Tech

- **Vanilla JS** — no frameworks, no bundler
- **NHL Web API** — `api-web.nhle.com/v1/roster/{TEAM}/current` for live rosters
- **localStorage** — save/load game state
- Single HTML file, ~150KB

---

## License

MIT — do whatever you want with it.
