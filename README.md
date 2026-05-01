# Tokyo Oasis 🌿 | Daily Exhibition & Escape Curator

### **Cutting through the noise. Finding the quiet.**

Tokyo Oasis is a self-hosted, fully automated daily curation engine that scans Tokyo's cultural landscape and delivers a personalized, distraction-free shortlist of exhibitions and peaceful escapes — straight to your phone, every morning.

---

## 🧩 Product Vision: The Core Insight

* **The Problem**: Tokyo is full of things to do, but most recommendation platforms are optimized for popularity — not for people who want quiet, thoughtful experiences. Scrolling through endless "Top 10" listicles to find one genuine exhibition is its own kind of cognitive drain.
* **The Solution**: A **rule-based personal curation system** built around a simple principle — filter for signal, suppress noise. Instead of showing everything, Tokyo Oasis is tuned to a specific set of personal preferences.

---

## ⚡ How It Works

### 1. Daily RSS Scan & Scoring

Each morning, the engine fetches content from curated Tokyo cultural feeds and scores each item using a custom relevance model:

* **+30** — Contains exhibition / art / museum keywords
* **+60** — Located in a Tokyo core area (Ginza, Ueno, Roppongi, Shibuya...)
* **+50** — Free entry, design-focused, or stationery-related
* **−40** — Located outside Tokyo (Kyoto, Osaka, overseas...)
* **−60** — Detected as a ranking post, "best of" listicle, or aggregator content
* **−80** — Semantic duplicate detected (same headline prefix appearing multiple times)

Only items scoring above threshold are considered. The top 5 are selected for delivery.

### 2. Semantic De-duplication

A prefix-based de-duplication layer prevents any single source from dominating the feed. If multiple entries share the same opening characters, subsequent matches are heavily penalized — keeping the daily digest genuinely diverse.

### 3. Fallback: The Quiet Park

On days when no exhibitions meet the quality bar, Tokyo Oasis doesn't send noise. Instead, it selects a quiet, well-regarded park or outdoor space from a curated local database — a gentle nudge to step outside anyway.

### 4. Push Notification via Bark

Filtered results are delivered through [Bark](https://bark.day.app/), a privacy-first iOS push notification service. No accounts, no tracking, no third-party servers involved.

---

## 📱 Demo

<p align="center">
  <img src="https://github.com/user-attachments/assets/5c5aa632-49fa-4875-a2ab-b2a2763c9838" width="250"/>
  <img src="https://github.com/user-attachments/assets/79842af3-a687-4ae4-abc6-1d6285bbad56" width="250"/>
</p>
<p align="center"><em>Daily push notification · Top 5 curated results</em></p>

---

## 🛠️ Technical Highlights

* **RSS Parsing**: `feedparser` handles multi-source ingestion with graceful timeout and error recovery per feed
* **Scoring Engine**: Custom rule-based relevance model with YAML-based configuration — locations, keywords, junk filters, and fallback database all live outside the codebase, requiring zero code changes to retune.
* **History Persistence**: JSON-based deduplication log prevents repeat notifications across days
* **URL Safety**: Bark payloads are aggressively sanitized and truncated before encoding, ensuring reliable GET request delivery regardless of source content quality
* **Scheduled Execution**: Runs via GitHub Actions on a daily cron schedule — zero infrastructure, zero maintenance cost
* **End-to-end ownership**: Designed and implemented the full pipeline independently, from scoring logic and filtering rules to automation workflow

---

## 💭 Why I Built This

I moved to Tokyo and quickly realized that the city has extraordinary cultural offerings — but finding them requires wading through an enormous amount of curated-for-everyone, useful-for-no-one content.

I wanted something that matched my specific taste: quiet spaces, genuine exhibitions, no crowds if possible. So I built a small engine that does exactly that, tuned entirely to my preferences, and delivers it before I've had to think about it.

It's a small project, but it's one I actually use every day.

---

*© 2026 Lan. Built for personal use. Tuned for quiet.*
