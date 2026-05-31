# Workflow: Morning Brief

**Objective:** Send a daily 8am email to Bryan summarising today's calendar events and ClickUp tasks.
**Tool:** `tools/morning_brief.py`
**Output:** Email to bryansdesignstudio@gmail.com

---

## Inputs required

| Input | Source | Status |
|-------|--------|--------|
| Google Calendar (today's events) | OAuth token.json | Connected |
| ClickUp tasks (due today + overdue) | `.env` CLICKUP_API_KEY | Connected |

---

## Phase 1 — Run manually (Bike Method)

Before scheduling, validate the output is useful:

```bash
python3 tools/morning_brief.py
```

It will preview the brief and ask before sending. Run this for 3-5 days. If it's useful, proceed to Phase 2.

---

## Phase 2 — Schedule at 8am (macOS launchd)

Once validated, create a launchd plist to run it automatically:

1. Create the file `~/Library/LaunchAgents/com.aios.morningbrief.plist`:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
  <key>Label</key>
  <string>com.aios.morningbrief</string>
  <key>ProgramArguments</key>
  <array>
    <string>/Library/Developer/CommandLineTools/usr/bin/python3</string>
    <string>/Users/bryan_gallagher/Documents/VS Studio Master/AIS-OS/tools/morning_brief.py</string>
    <string>--send</string>
  </array>
  <key>StartCalendarInterval</key>
  <dict>
    <key>Hour</key>
    <integer>8</integer>
    <key>Minute</key>
    <integer>0</integer>
  </dict>
  <key>StandardOutPath</key>
  <string>/tmp/morning-brief.log</string>
  <key>StandardErrorPath</key>
  <string>/tmp/morning-brief-error.log</string>
</dict>
</plist>
```

2. Load it:
```bash
launchctl load ~/Library/LaunchAgents/com.aios.morningbrief.plist
```

3. To unload/stop:
```bash
launchctl unload ~/Library/LaunchAgents/com.aios.morningbrief.plist
```

---

## Edge cases

- **No tasks due:** brief says "Nothing due. Good day to get ahead."
- **No calendar events:** brief says "Nothing scheduled."
- **API error:** script exits with error message — check `.env` keys and `token.json`
- **Token expired:** delete `token.json` and re-run `python3 tools/google_auth.py`

---

## Next expansions (when ready)

- Add Outlook calendar (medical practice) once Microsoft API is connected
- Add Gentu/Xero daily revenue snapshot
- Upgrade to HTML email with better formatting
