# Driver Route Assist – how to use

© 2026 Gary Bennett. All rights reserved. See LICENSE.

Two web pages, nothing to install on the tablets:

| File | Who | What |
|---|---|---|
| `index.html` | Regular driver | Records the round. **REVERSE** turns the line red, **TRAVEL** turns it purple. |
| `viewer.html` | Relief driver | Shows a recorded round: green = collecting, red = reverse down, purple = travel to next area, arrows show the order. |

The recording is saved on the tablet as it goes, so closing the browser or a crash
doesn't lose it — reopen the page and it carries on.

---

## 1. Put the pages online (once)

The tablet only lets a web page use GPS if the page is on a secure (https) address.
Free option, about 10 minutes:

1. Make a free account at **github.com**.
2. Top right **+ → New repository**. Name it e.g. `bin-routes`, tick **Public**, **Create**.
3. **uploading an existing file** → drag in `index.html` and `viewer.html` → **Commit changes**.
4. **Settings → Pages** → Source: **Deploy from a branch**, Branch: **main**, folder **/ (root)** → **Save**.
5. After a minute the page shows your address, e.g. `https://yourname.github.io/bin-routes/`

   - Recorder: `https://yourname.github.io/bin-routes/`
   - Viewer:   `https://yourname.github.io/bin-routes/viewer.html`
   - Practice mode (fake lorry, no driving): add `?demo` → `https://yourname.github.io/bin-routes/?demo`

The pages themselves hold no route data — each round stays on the tablet until someone sends the files.

On each tablet: open the recorder address in Chrome → **⋮ → Add to Home screen**, so it's one tap.

## 2. Regular driver – recording a round

Split screen: bin-report app on one side, Round Recorder on the other
(Galaxy Tab: open the recent-apps button, tap the Chrome icon → **Open in split screen view**).

1. Type the round name, tap **START** at the depot. First time only: tap **Allow** for location.
   The drive out to the first street records in **purple** (travelling).
2. **At the first street: tap COLLECTING.** The line draws **green** from there.
3. **Before reversing down a street: stop, tap REVERSE.** The bar and line turn **red**.
4. **After reversing: stop, tap DONE REVERSING.** Back to green.
5. **Leaving one area for the next: tap TRAVEL.** The line turns **purple** (not collecting).
   **Arriving at the next area: tap COLLECTING.** Back to green.
   (REVERSE still works while travelling; DONE REVERSING goes back to purple.)
6. **Tip run or break: tap PAUSE.** Nothing is recorded and the screen can sleep.
   Back where you left the round: **tap RESUME** – it carries on in the same colour as before.
   The map shows **⏸ Tip 1** where you paused and **▶ Resume 1** where you carried on, with no line to the tip.
7. Last street done: tap **TRAVEL** for the drive back (or **PAUSE** if the round ends with a tip run),
   then at the depot **FINISH** → **TAP AGAIN** to confirm.
8. **Share / send files** → email or WhatsApp the files to whoever sets up the relief map.

| Line | Meaning |
|---|---|
| Green | Collecting, driving forward |
| Red | Reverse down this street |
| Purple | Travelling to the next area (not collecting) |
| Grey dashes | Not recorded – route unknown |

**Screen:** while recording, the page keeps the screen on by itself – the status bar shows
**"Screen kept on ✓"**. If it says **"Screen may sleep"**, tap the map once; if it still says it,
set the tablet's screen timeout to 30 minutes. **Don't press the power button while recording** –
a web page can't record with the screen off (that stretch shows as "Not recorded").
Keep the tablet on its cab charger.

**Keep the recorder visible while driving.** Any of these is fine:
- **Split screen** – recorder and bin app side by side.
- **Pop-up view** – bin app full screen, recorder as a small floating window on top
  (recent-apps button → tap the Chrome icon → **Open in pop-up view**; drag the corner to resize).
- Switching the bin app to full screen **while stopped** to log a report, then switching back.

If the recorder is hidden while the lorry is **moving**, the tablet pauses its GPS. That stretch
shows as a **grey dashed "Not recorded"** line (never as a green route), the stats bar shows
"Not recorded", and the driver sees a yellow warning when they switch back. If a round has
big grey gaps, record it again.

Only tap while stopped. Tablet in its cradle.

## 3. Relief driver – seeing the round

**Option A – inside Google Maps (uses the `.kml` file, keeps green/red):**
1. On a PC go to **google.com/mymaps** → **Create a new map** → **Import** → choose the round's `.kml`.
2. Name the map after the round. **Share** it with the relief drivers' Google account.
3. On the tablet: **Google Maps → You / Saved → Maps** → open the round. It shows over the normal map with the blue dot.

If Google shows the lines in one colour, click the layer's paint-roller icon →
**Style by: name**, and set Collecting = green, Reverse = red, Travel = purple.

**Option B – the viewer page (uses the `.gpx` file):**
open `viewer.html`, tap **Open round…**, pick the `.gpx`. **Show me** adds your live position.
Red circles **R1, R2…** mark where each reverse starts — tap one for a note.
Where the lorry reverses in and then drives back out the same street, the street shows
**two lanes side by side**: red with arrows pointing in, green (or purple) with arrows pointing out.
Grey dashed lines mean that bit wasn't recorded — the route there is unknown.
**⏸ Tip 1 / ▶ Resume 1** mark a tip run: go to the tip your usual way, then pick the round up at ▶ Resume.
While **Show me** is on, the viewer keeps the screen on too.

The relief driver can switch between the viewer and the bin app however they like
(full screen, split, pop-up) — viewing doesn't record anything, so nothing is lost.

## Test it on this PC now
In a terminal in this folder:

    python -m http.server 8123

then open `http://localhost:8123/?demo` (fake lorry drives a loop — try REVERSE / FINISH /
Download) and `http://localhost:8123/viewer.html` to open the file you downloaded.

## Before using it for real
- Get the council / contractor's OK to record rounds, and the regular drivers' agreement.
- Check the tablets can open ordinary websites (IT sometimes locks council devices down).
