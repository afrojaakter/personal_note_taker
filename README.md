# Founder Tasks

A voice-first personal task tracker built for solo founders. Brain-dump out loud, get tasks split + dated + categorized automatically. Installable on your phone and desktop as a PWA.

## What's in this folder

```
personal_note_taker/
├── index.html        ← the app
├── manifest.json     ← PWA manifest
├── sw.js             ← service worker (offline support)
├── icon.svg          ← app icon
├── icon-maskable.svg ← Android adaptive icon
└── README.md         ← this file
```

## Host it for free (so you can use it on your phone)

### GitHub Pages — recommended, ~5 minutes

GitHub Pages gives you a permanent, free URL you control. Everything below is web-only — no command line.

1. **Sign in to GitHub.** Go to https://github.com and sign up if you don't have an account.
2. **Create a new repository.**
   - Click the **+** in the top-right → **New repository**.
   - Name it `personal_note_taker` (same as your local folder).
   - Visibility: **Public** (required for free GitHub Pages).
   - Check **"Add a README file"** (you'll replace this in a second).
   - Click **Create repository**.
3. **Upload the app files.**
   - On your new repo's page, click **Add file → Upload files**.
   - Drag in every file from this folder: `index.html`, `manifest.json`, `sw.js`, `icon.svg`, `icon-maskable.svg`, `README.md`. (Drag the files, not the folder, so they end up at the repo root.)
   - Scroll down, click **Commit changes**.
4. **Enable Pages.**
   - In the repo, click **Settings** (top tabs).
   - In the left sidebar, click **Pages**.
   - Under "Build and deployment", set **Source** to **Deploy from a branch**.
   - Branch: **main**, folder: **/ (root)**. Click **Save**.
5. **Wait ~1 minute, then open your site.**
   - Refresh the Pages settings page. A green box will appear with your URL, like `https://<your-username>.github.io/personal_note_taker/`.
   - (If you see "Your site is being built", just wait 30–60 seconds and refresh.)
6. **Install on your phone.**
   - Open the URL on your phone.
   - **iPhone (Safari)**: tap the **Share** button (square with up-arrow) → **Add to Home Screen** → **Add**.
   - **Android (Chrome)**: tap the **⋮** menu → **Install app** (or **Add to home screen**).

Done. The app icon now lives on your home screen, opens full-screen, and works offline. To update later: drag new files onto the same repo (Add file → Upload files), commit, and the site re-deploys in about a minute.

### Netlify Drop — alternative, ~30 seconds, no account needed

If you don't want a GitHub account, Netlify Drop is a free drag-and-drop hosting service. Go to https://app.netlify.com/drop and drag the entire folder onto the page. You instantly get a public URL.

### Just want a quick try?

You can also open `index.html` directly in your desktop browser (double-click it). Voice, tasks, and reminders all work. The only limitations of local-file mode: no PWA install button, and Chrome may re-ask for mic permission each session. Hosting fixes both.

---

## How to use it

### Brain-dump voice mode

Tap the 🎙 mic button. The button pulses red and a transcript appears below the input. Talk for as long as you want — pause to think, take a breath, the app keeps listening. Click the mic again to stop.

When you stop, the app:
1. Splits what you said on sentence breaks (periods, "and then", "also", "after that") into separate tasks.
2. For each one, detects the date/time ("tomorrow at 5pm", "Friday", "in 3 days", "every Monday").
3. Detects the category (Build, Customer, Investor, Networking, Event, Mentor, Research, General).
4. Adds them all in one go and switches to the All view so you can see what landed.

Examples to try:
- *"Email three furniture retailers tomorrow. Prep investor deck by Friday. And remind me to follow up with Sarah next Monday at 10am."*
- *"Austin Startup Week event on June 3rd at 6pm. Coffee chat with mentor every Tuesday."*

### Status: To Do → Doing → Done

Click the circle on the left of any task:
- **Empty** = To Do
- **Pulsing dot** = Currently Working On (it appears at the top of Today and All views)
- **Checkmark** = Done

Each click cycles to the next state. Cycle back to To Do from Done if you need to reopen.

### Categories — how they work

Every task lives in one of eight categories, shown as a colored pill on the task: **Build**, **Customer**, **Research**, **Network**, **Mentor**, **Investor**, **Event**, **General**.

Three things happen with categories:

1. **Auto-tagging on creation.** The app scans the text for keywords. "investor" → Investor, "retailer"/"customer" → Customer, "mentor" → Mentor, "meetup"/"RSVP"/"Austin Startup Week" → Event, "build"/"deploy"/"fix" → Build, "research" → Research, "coffee chat"/"intro to" → Network. Anything that doesn't match becomes General.
2. **Changing it manually.** Click the colored pill on any task — a dropdown opens with all eight categories. Pick one. The color updates immediately.
3. **Filtering.** The row of colored chips above the task list filters the visible tasks. Click **Investor** to see only investor tasks; click **All** to clear the filter. The Month and Timeline views also color-code each task by category, so at a glance you can see whether a day is heavy on Customer outreach vs. Build work.

### Events with location + RSVP link

Tasks tagged Event get extra fields. Click **+ Details** on an event card and fill in:
- 📍 Location (e.g., "Capital Factory, 701 Brazos St")
- 🔗 RSVP URL (Luma, Eventbrite, etc.)

The **Events** view shows just your event list — upcoming and past.

### Recurring tasks

Set a recurrence (Daily / Weekly / Monthly) on any task. When you mark it done, it automatically re-creates the next instance with the new date. Say "every Monday" or "daily" in voice mode and the app sets recurrence for you.

### Reminders

The app uses browser notifications. The first time it asks for permission, allow it. Tasks with a specific time pop a notification when due; tasks due today (no time set) get a morning notification.

### Data + export

Everything saves to your browser's local storage. To back up or move devices: **Export** (bottom of page) downloads a JSON file. **Import** merges a file back in.

---

## Sharing with others

Each person who installs the app has their own local task list — tasks don't sync between devices through the app itself. If you want to share the *tool* with another founder, send them the hosted URL. They'll install their own copy with their own tasks.

If you want to sync your tasks across your laptop and phone, the simplest workflow is: Export from one, Import into the other.

---

## Troubleshooting

**Mic asks for permission every time** → Happens with `file://`. Once you host it via GitHub Pages / Netlify, the browser remembers permission per origin.

**Mic stops after a long pause** → The app auto-restarts the recognizer when the browser cuts it off mid-session, so you should be able to pause freely. If you find it dropping, click the mic to stop, then click again to resume — the buffer carries over.

**Brain-dump didn't split my tasks** → It splits on sentence-ending punctuation and connector phrases ("and then", "also", "after that"). Note: bare "next" does NOT split (it's almost always part of "next Monday" / "next week"). If everything runs together, try ending each task with a period or saying "and then".

**Notifications don't appear** → Check browser settings. On iOS, you need to install the app to Home Screen first; Safari doesn't deliver web notifications otherwise. On Mac/PC, the browser tab needs to be running (it can be in the background).

**Want to wipe everything and start fresh** → Open DevTools (F12) → Application → Local Storage → delete the `founder_tasks_v2` key.
