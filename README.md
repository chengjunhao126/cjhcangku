<div align="center">
  <img alt="logo" height="120" src="./public/favicon.png" width="120"/>
  <h2>Today's Hot List</h2>
  <p>Aggregating hot topics from across the web, all in one place.</p>
  <br />
  <img src="./screenshots/main.jpg" style="border-radius: 16px" />
</div>
<!-- by 程俊豪 -->
User Guide for "Today's Hotlist"
1. Feature Modules
1. Multi-source Content Aggregation
The system integrates real-time trending data from multiple mainstream content platforms. A backend crawler scheduler fetches and caches data periodically, while the frontend retrieves and displays it via unified RESTful APIs. Supported platforms include (but are not limited to):

Bilibili – Popular videos, trending discussions, and user interactions;

Weibo – Hot search keywords and trending hashtags;

Douyin (TikTok China) – Popular short video topics;

Zhihu – High-traffic Q&A threads (with built-in error handling);

Others – Including Baidu Hot Search, 36Kr Flash News, Xiaohongshu, ITHome, and Sspai.

2. Live Refresh Logic
Each module includes a timestamp indicating the last update time. Data is refreshed via both automatic and manual triggers:

The backend uses scheduled cron jobs to refresh cached content every 10 minutes;

The frontend allows users to manually trigger a forced HTTP request to refresh UI content via the refresh button.

3. UI Controls

🔄 Manual Refresh – Sends an immediate request to update all modules;

🌙/☀️ Theme Toggle – Switch between light and dark modes; preferences are stored via localStorage;

⚙️ Settings Panel – Open the configuration menu to toggle visibility of each content module;

🔁 Retry Mechanism – If a data fetch fails, the corresponding module will show a fallback error card with a retry button to re-trigger the API request.

2. Frequently Asked Questions (FAQ)
Q1: Why does a module show "Failed to Load"?
A: Possible causes include:

Target platform's page structure (HTML/JSON) has changed;

Network issues (e.g. timeouts, DNS errors);

IP or user-agent blocks.
Troubleshooting Tips:

Check your internet connection;

Click the “Retry” button in the failed module;

Open the browser console (F12) for detailed logs and report errors if necessary.

Q2: The content hasn’t updated for a long time — what should I do?
A:

Try a hard refresh (Ctrl+F5) to bypass browser caching;

The server may still be within its cache window (e.g., last 10-minute interval);

Enable “Developer Mode” in settings to inspect raw API timestamps per module.

Q3: Why is the "x minutes ago" time incorrect?
A: The timestamp is calculated using the browser’s local Date.now(). If your system time is incorrect, the relative time display will be inaccurate. Please sync your system clock.

Q4: Can I click on keywords to view the original source?
A: Some platforms (e.g., Weibo, Zhihu) support outbound links. This feature can be enabled via the "Link Redirect" option in Settings. Others may not support it due to anti-scraping protection or missing URLs in source data.

3. Best Practices
✅ Check the hotlist during peak periods (e.g., 7–9 AM, 12–1 PM) to capture trending topics efficiently;

✅ Temporarily disable unstable modules in Settings if they frequently fail to load, which helps performance;

✅ Use a modern browser (Chrome 90+, Edge, Firefox) to ensure compatibility and smooth experience;

✅ For embedding use cases, wrap the application as an iframe or extract components for modular use;

✅ Use the Feedback button in Settings to report bugs or suggest new feature enhancements.
<!-- by 程俊豪 -->
