🛡️ Cybersecurity Workshop — Feedback System

A real-time, browser-based feedback collection and live dashboard system built for cybersecurity workshops. No server required. No database required. Works fully offline.


📁 File
cybersecurity-feedback.html   ← Single file. Open this in any browser.

🚀 How to Use
For Participants (Submit Feedback)

Open cybersecurity-feedback.html in any browser
Wait for the boot screen, then tap to enter
Click "SUBMIT FEEDBACK" tab
Select a star rating (1–5)
Optionally tap emoji reactions and type a message
Press "◈ TRANSMIT FEEDBACK ◈"
Your feedback is instantly saved and visible on the live dashboard

For Organizers (View Feedback)

Open cybersecurity-feedback.html in any browser on the same device
The app opens directly on the Dashboard page
All submitted feedback appears live in the feed
Switch between NEWEST and TOP RATED sort views
The dashboard auto-refreshes every 3 seconds


✨ Features
Dashboard (Index Page)
FeatureDescription📊 Live StatsTotal reports, average rating, today's count📈 Rating ChartBar chart showing distribution of 1–5 star ratings📡 Live FeedAll feedback displayed as cards, newest first🟢 New FlashGreen glow animation on newly arrived entries🔢 Sort OptionsSort by Newest or Top Rated📜 Ticker TapeScrolling preview of latest feedback at the top🔄 Auto-RefreshDashboard polls for new entries every 3 seconds
Feedback Form
FeatureDescription⭐ Star Rating1–5 star animated rating selector😀 Emoji Dock20 emoji reactions insertable into the text field📝 Text FieldUp to 500 characters of free-text feedback🔐 Encrypted BadgeVisual trust indicator for participants✅ Success ScreenAnimated confirmation with unique Operation ID↩️ Quick Return"View Live Feed" button after submission
Visual Design

Gold matrix code rain background animation
CRT scanlines and vignette overlay
Boot screen with simulated system logs
Orbitron + Share Tech Mono + Exo 2 typography
Fully responsive for mobile and desktop


💾 Storage — How Feedback is Saved
Feedback is stored using localStorage — the browser's built-in key-value storage.
Storage Key:  cyberws_feedbacks_v1
Location:     Browser localStorage (on the device running the HTML file)
Format:       JSON array of feedback objects
What Each Feedback Entry Stores
json{
  "id":     "OP-X7K2MN-A4F1",
  "rating": 4,
  "text":   "Great session on phishing tactics! Very practical.",
  "emojis": ["🔥", "💡"],
  "time":   1741234567890
}
FieldDescriptionidUnique Operation ID (auto-generated)ratingStar rating from 1 to 5textFull text of the feedback messageemojisArray of emoji reactions extracted from the texttimeUnix timestamp (milliseconds) of submission
Storage Limits & Behavior
PropertyDetailCapacity~5 MB per browser origin (typically 500–1000+ entries)PersistenceSurvives page refresh and browser restartScopeSame browser + same device onlyShared accessMultiple tabs on the same browser share the same dataCross-device❌ Not shared between different devices
Exporting Feedback Data
To export all stored feedback, open the browser Developer Console (F12 → Console tab) and run:
javascript// View all feedback as JSON
console.log(JSON.parse(localStorage.getItem('cyberws_feedbacks_v1')));

// Copy to clipboard
copy(localStorage.getItem('cyberws_feedbacks_v1'));

// Download as a .json file
const data = localStorage.getItem('cyberws_feedbacks_v1');
const blob = new Blob([data], { type: 'application/json' });
const a = document.createElement('a');
a.href = URL.createObjectURL(blob);
a.download = 'workshop_feedback.json';
a.click();
Clearing All Feedback
javascript// Run in browser console to wipe all saved feedback
localStorage.removeItem('cyberws_feedbacks_v1');

🌐 Deployment Options
Option A — Local (Single Device)
Just open the .html file directly in a browser. All feedback submited on that device is stored and viewable on that device.
Option B — Local Network (Multiple Devices)
Host the file on a simple local HTTP server so participants on the same Wi-Fi network can submit from their phones:
bash# Python (recommended)
python -m http.server 8080

# Node.js
npx serve .

# Then open on any device on the same network:
# http://<your-ip>:8080/cybersecurity-feedback.html

⚠️ Note: In this mode, each device stores feedback in its own localStorage. To collect all feedback, use the organizer's device as the submission point, or use Option C below.

Option C — Shared Live Feed (Recommended for Events)
For real-time cross-device sharing, host the file on any static web host:
HostFree TierHowGitHub Pages✅ YesPush to repo → enable PagesNetlify✅ YesDrag & drop the .html fileVercel✅ Yesvercel deployCloudflare Pages✅ YesConnect GitHub repo

When hosted on a shared URL, all participants submit to the same URL. The organizer opens the same URL to watch feedback arrive live.


🔧 Customization
Change Workshop Name
Find and replace in the HTML file:
CYBERSECURITY WORKSHOP 2025  →  YOUR EVENT NAME 2025
Change Rating Labels
In the JavaScript section, find:
javascriptconst rLbls = ['', '// POOR PERFORMANCE', '// BELOW EXPECTATIONS', '// MEETS STANDARDS', '// EXCEEDS STANDARDS', '// ELITE — OUTSTANDING'];
Replace with your own labels.
Change Emoji Reactions
Find the emoList array and update with your preferred emojis:
javascriptconst emoList = [{e:'❤️'},{e:'🔥'},{e:'💡'}, ...];
Change Color Theme
Edit the CSS variables at the top:
css:root {
  --gold:  #FFD700;   /* Primary accent color */
  --green: #00FF88;   /* Live / success color */
  --red:   #FF1A2E;   /* Alert / warning color */
  --blue:  #00D4FF;   /* Secondary accent */
}

📋 Browser Compatibility
BrowserSupportChrome / Edge 80+✅ FullFirefox 75+✅ FullSafari 13+✅ FullMobile Chrome / Safari✅ FullInternet Explorer❌ Not supported

⚙️ Technical Details

Zero dependencies — no npm, no build step, no backend
Single HTML file — everything is self-contained
Storage engine — browser localStorage (JSON)
Auto-refresh — setInterval polling every 3 seconds
Fonts — loaded from Google Fonts CDN (requires internet on first load; cached after)
Canvas animation — gold matrix rain via HTML5 Canvas API


📄 License
Free to use and modify for educational and workshop purposes.

Built for Cybersecurity Workshop 2025 — Secure Feedback Terminal v3.0.0# Feedback-
