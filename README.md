# Kim-Leitner Recall Engine

A zero-dependency, client-side memory training application synthesizing three active recall methodologies:
1. **Kim's Game:** Timed visual exposure to an item array followed by complete stimulus removal.
2. **Blurting Method:** Unprompted, uncued retrieval dump into an open text buffer.
3. **Leitner System:** Spaced repetition scheduling advancing successful cards into longer interval boxes and demoting misses to high-frequency review.

---

## Cognitive Mechanics & Daily Workflow

To avoid working memory priming and preserve long-term synaptic consolidation, the application is strictly designed for **one session per day (~2–3 minutes)**.

```
┌─────────────────────────────────────────────────────────────┐
│ 1. Kim's Exposure (30s)                                      │
│    Study 10 words (Due Leitner cards + Deterministic seed). │
└──────────────────────────────┬──────────────────────────────┘
                               │ (Wipe viewport)
                               ▼
┌─────────────────────────────────────────────────────────────┐
│ 2. Blurting Phase (60s)                                     │
│    Rapid, free-form retrieval dump into input buffer.       │
└──────────────────────────────┬──────────────────────────────┘
                               │ (Diff & evaluate)
                               ▼
┌─────────────────────────────────────────────────────────────┐
│ 3. Leitner Resolution                                       │
│    Hits: Advance (Box n+1, up to Box 5).                    │
│    Misses: Reset to Box 1 (Tested next day).                │
└─────────────────────────────────────────────────────────────┘
```

### Leitner Interval Tiers
| Tier | Review Interval | Description |
| :--- | :--- | :--- |
| **Box 1** | 1 day | Daily review (new words or missed reviews) |
| **Box 2** | 3 days | Short-term consolidation |
| **Box 3** | 7 days | Medium-term retention |
| **Box 4** | 14 days | Long-term memory threshold |
| **Box 5** | 30 days | Mastered retention |

---

## Technical Architecture

- **Zero-Dependency Static Runtime:** Single [index.html](index.html) file containing semantic HTML, CSS custom properties (dark slate theme), and vanilla ES6+ JavaScript. No build step, node runtime, or external CDN dependencies required.
- **Deterministic Seeding:** Uses a Mulberry32 pseudo-random number generator (PRNG) seeded by a 32-bit hash of the current ISO date (`YYYY-MM-DD`). Every user receives identical new words on any given calendar day.
- **Persistent State:** Stores box tiers, intervals, and historical timestamps in `localStorage` under `kim_leitner_v1`.
- **Vocabulary Bank:** Embedded, categorized corpus of 300+ concrete and conceptual nouns.

---

## Usage & Deployment

### Local Execution
Open `index.html` directly in any standard browser:
```powershell
# Double-click index.html or launch via Python local server:
python -m http.server 8080
```
Then navigate to `http://localhost:8080`.

### Android / Mobile Usage
To play on Android with persistent `localStorage` and a standalone full-screen interface:
1. Deploy this repository to **GitHub Pages** (Settings $\to$ Pages $\to$ Source: `main` branch $\to$ Save).
2. Open the published HTTPS URL in mobile Chrome.
3. Tap **Menu (⋮) $\to$ Add to Home screen**.

---

## License
MIT
