# VibeCraft Campus Hub

One website that hosts both VibeCraft tools for SRM IST Tiruchirappalli (Faculty of Engineering and Technology):

| Tool | Dimension | What it does |
|------|-----------|--------------|
| **Attendance Predictor** (Round 1) | Overworld | How many classes you must attend to stay above 75% (or reach 90%), an irreversible-detention alert, charts, an OD / leave simulator and the Attendance Advisor chat. |
| **Room Locator** (Round 2) | The End | Empty rooms right now, floor by floor, a rotatable 3D building map with a live countdown to the next class, a plain-English room finder, and a "Call the Squad" WhatsApp invite. |

The hub (`index.html`) has a hotbar to switch tools, a home page with both, and a shared favicon. Each tool keeps its own dimension theme. Switching tools does not lose your inputs, because both stay loaded once opened.

## Use it

- `#/` home · `#/attendance` · `#/rooms` (deep links work)
- Press **1**, **2** or **3** to switch tools.
- Each tool also works on its own: `apps/attendance.html`, `apps/rooms.html`.

## Run locally

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

No build step or dependencies. Open it through a server (not by double-clicking the file) so the hub can load the two tools.

## Deploy to GitHub Pages

Push to `main`, then **Settings -> Pages -> Source -> GitHub Actions** (workflow included). Or choose **Deploy from a branch -> main / (root)** and delete `.github`.

## Structure

```
index.html              hub: hotbar, home page, loads the tools
apps/attendance.html    Attendance Predictor
apps/rooms.html         Room Locator
data/                   timetables (CSV + JSON) used by the Attendance Predictor
favicon.svg / .ico      Eye of Ender favicon, apple-touch-icon.png
```

## Notes

- Attendance Predictor: 14 sections (I-IV year). Details, maths and the chatbot notes are inside the app. Default holiday list has only 2 Oct 2026, so edit it for your college.
- Room Locator: built from the 9 sections that list rooms (II-IV year, 2026-27). The I-year sheets name no rooms. AC rooms are placeholders: edit the `AC` set in `apps/rooms.html`. The room finder is a local rule-based parser.
- The Attendance Advisor uses a built-in parser on GitHub Pages. To use an LLM, add a small backend and never put an API key in front-end code.
- Fonts (Press Start 2P, VT323) load from Google Fonts and fall back to monospace offline.

## License

MIT
