# Kinora Form Coach

A standalone app, separate from the kinorafit.online website. Clients film themselves (live camera or an uploaded video) or take a photo.
The app tracks 33 body points with Google MediaPipe Pose, measures joint angles in real time, counts reps, speaks
correction cues, and at the end shows a full report: score, key frames, faults sorted by priority, biomechanics
table (angles vs target ranges), rep-by-rep chart, body map and the anatomy of the movement. Clients can save it as a PDF
or send a summary to you on WhatsApp.

- **Exercises:** squat, lunge, hip hinge, glute bridge, push-up, knee push-up, plank, overhead press, posture check.
- **Daily limit:** 60 minutes of video analysis per day per device. It resets at midnight. Photos are unlimited.
- **Updates every day:** the home screen shows a new daily focus (the client's most frequent fault this week and a drill), an exercise of the day, a tip, a 14-day progress chart and a streak.
- **Private:** everything runs on the phone. Videos are never uploaded; history stays on the device.
- **Install:** on the phone, open the page and choose *Add to Home Screen*. It then works like an app.

| I want to change… | Where |
|---|---|
| Fault texts, cues, anatomy, drills, daily tips | `js/knowledge.js` (text only) |
| Angle thresholds, exercises | `js/exercises.js` |
| Daily limit (60 min) | `DAILY_LIMIT_SEC` at the top of `js/app.js` |
| WhatsApp number for reports | `COACH_WA` at the top of `js/app.js` |

Limits to know: the analysis comes from a phone camera (2D image + AI), so it is very good but never 100% exact;
results depend on light, camera angle and clothing. The 60-minute limit is stored on the device, so a client who clears
their browser data gets a fresh allowance; enforcing it strictly needs user accounts and a server.
The AI engine and models in `vendor/` and `models/` are Apache-2.0 (see `vendor/mediapipe/NOTICE.txt`).

## Publish (GitHub Pages, free)

Push this folder to the `main` branch of its own repository, then on GitHub:
**Settings → Pages → Build and deployment → Source: GitHub Actions**. The app goes live at
`https://<your-user>.github.io/<repository-name>/` and updates on every push to `main`.
It must be served over HTTPS for the camera to work (GitHub Pages does this automatically).
