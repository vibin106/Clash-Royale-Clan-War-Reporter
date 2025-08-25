# Clash Royale Clan Report Automation (n8n Workflow)

## 📌 Overview
This **n8n workflow** automates the process of **monitoring a Clash Royale clan**, generating insightful reports, and sending them to the clan leader via **Telegram**. It integrates the **Clash Royale API** with **Google Gemini AI models** to analyze player activity, battle performance, and inactivity, then formats this into friendly and actionable summaries.

---

## ✅ Features
- **Automated Daily Trigger** – Runs at a scheduled time every day.
- **Clash Royale API Integration** – Fetches clan member data and battle logs.
- **AI-Powered Analysis** – Uses **Google Gemini** to:
  - Create top-player summaries.
  - Draft motivational messages for inactive players.
  - Suggest actions for long-term inactive members.
- **Reports on Key Metrics**:
  - Clan War participation.
  - Top 3 players based on recent battles.
  - Inactive players (more than 3 days).
- **Telegram Notifications** – Sends the final report directly to a clan leader.

---

## 🛠 Workflow Structure
### **Trigger**
- **Schedule Trigger** – Executes daily at **11:00 AM**.

### **Core Steps**
1. **Get Clan Members** – Fetch member list from **Clash Royale API**.
2. **Fetch Battle Logs** – Retrieve recent battle history for each player.
3. **Process & Analyze**:
   - Identify **war skippers** (did not play today’s Clan War).
   - Calculate **top performers** (last 3 battles, number of wins).
   - Detect **inactive players** (no battles for 3+ days).
4. **AI Summaries (Google Gemini)**:
   - **Clan War Agent** – Motivational note for war skippers.
   - **Ranking Agent** – Summary of top 3 players.
   - **Inactive Agent** – Suggestions for inactive players.
5. **Combine Reports** – Merge all insights into one structured message.
6. **Send via Telegram** – Deliver the final report to the leader.

---

## 🔍 Data Flow Diagram
*(You can add an image of your workflow from n8n UI here)*  
Example:
```
Schedule → Get Members → Battle Logs → Analysis → AI Summaries → Merge → Telegram
```

---

## ⚙️ Prerequisites
- **n8n** (self-hosted or cloud)
- **Clash Royale API Key**
- **Telegram Bot Token**
- **Google Gemini API Key** (PaLM or Gemini models)
- Node.js (if self-hosting n8n)

---

## 🚀 Setup Instructions
1. **Import the Workflow**
   - Open your **n8n dashboard**.
   - Click **Import** → Upload the provided JSON file (`Clash Royale.json`).
2. **Set Credentials**
   - **Clash Royale API**: Add your `Bearer` token in HTTP Request headers.
   - **Google Gemini API**: Configure `PaLM API` or Gemini credentials.
   - **Telegram**: Add your bot API token and target chat ID.
3. **Activate the Workflow**
   - Enable the workflow and schedule it.

---

## 🖥 Usage
- Once active, the workflow will **run daily at 11 AM**.
- The clan leader will receive:
  - ✅ **Top Player Rankings**
  - ✅ **Clan War Participation Summary**
  - ✅ **Inactive Player Alerts**
  - ✅ **Friendly Motivational Messages**

---

## 📦 Output Example
```text
📢 Clan Weekly Report 📢

🏅 Top Performer Highlights:
1. Player1 – 2 wins, 1 loss
2. Player2 – 3 wins
3. Player3 – 1 win, 2 losses

⛔ Inactivity Alert:
• PlayerX (Last played 5 days ago)
• PlayerY (Last played 7 days ago)

🎯 Coaching Tips:
Let's stay active and keep improving! 💪🔥
```
