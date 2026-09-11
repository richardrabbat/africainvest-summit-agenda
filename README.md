# AfricInvest AI Leadership Summit · Agenda

Live site: https://aisummit.lighty.ai/ (the github.io address redirects here)

A compact, attendee-facing agenda for the AfricInvest AI Leadership Summit (Tunis, 18 to 19 September 2026). One HTML file, no build step, no backend.

Source of truth for the schedule is the `AfricInvest_Program_Structure` Google Sheet. This site shows only what attendees need: time, session, who runs it, and links to the material.

## What it shows

- Day 1 and Day 2, with a direct link to each (`#day1`, `#day2`)
- Two tracks on split sessions: **Builder and roadmap** and **Debates and Hotseats**
- A track filter (Both / Builder and roadmap / Debates and Hotseats) that remembers the last choice on that device
- Session type colour coding: Inspiration, Foundational learning, Peer learning and problem-solving, Takeaways and roadmaps
- Material links (slides, sheets) that open in Google Drive, plus an "All material" index at the bottom
- Light and dark themes, phone-friendly layout

Facilitator kits, room setup, mic counts, story-arc stages and internal notes are deliberately left out.

## Updating the schedule

Everything lives in the `<script>` block at the bottom of `index.html`.

**Materials** are in the `MAT` object. Each entry is a Drive file id plus a display name and a type (`slides`, `sheet` or `doc`):

```js
opening: { n: "Opening slides", t: "slides", id: "1hn_nG1o..." },
```

**Sessions** are in `DAY1` and `DAY2`. A plenary session:

```js
{ s: "09:05", e: "09:20", cat: "insp", title: "Opening: who we are", who: "Richard", mat: ["opening"] },
```

A split session (one card per track):

```js
{ s: "10:30", e: "11:45", cat: "found", split: {
    b: { title: "AI fundamentals masterclass", who: "Richard", mat: ["fundamentals"] },
    d: { title: "Advanced AI masterclass", who: "Anthony and Jean-Claude" } } },
```

A break:

```js
{ s: "13:00", e: "13:45", brk: true, title: "Lunch", note: "Everyone back in the main room after lunch" },
```

`cat` is one of `insp`, `found`, `peer`, `take`. `note` is optional on any session or break.

## Before the summit

Attendees need view access to the linked files. Share the **Summit material** Drive folder (or each file) as "Anyone with the link can view", otherwise the links will ask for permission.

## Deploying

Hosted on GitHub Pages from the `main` branch. Every push goes live within a minute or two. Keep the `CNAME` file in the repo root: it holds the custom domain, and a push without it removes the domain from GitHub Pages.

```bash
git add index.html
git commit -m "Update agenda"
git push origin main
```

To preview locally, open `index.html` in a browser.
