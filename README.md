## SafeWeb – Cybersecurity SaaS for SMEs

Project Overview

SafeWeb is a cybersecurity SaaS platform designed to help small and medium-sized enterprises (SMEs) monitor, detect, and prevent cyber threats affordably. The platform provides real-time monitoring, vulnerability scanning, and security reports, enabling businesses to safeguard their networks and data.

## Features

### 1. Network Scan
- Scan IP addresses or domains.
- Choose between **Fast Scan** (top 100 ports) and **Full Scan** (all TCP ports).
- Display scan results in a scrollable, formatted view.
- Handles errors and shows loading states.

### 2. Monitoring
- View live status of monitored hosts (online/offline).
- Auto-refresh every 10 seconds.
- Displays last checked timestamp.
- Responsive table with color-coded status.

### 3. Settings
- Toggle **Dark/Light theme**.
- Theme selection persists across page reloads using `localStorage`.
- Notifications toggle (can be extended to persist).

---

## Tech Stack

- **Frontend**: HTMl, React, Tailwind CSS, Framer Motion
- **Backend**: FastAPI 
- **Icons**: Lucide React
- **Deployment**: GitHub Codespaces / VS code 

---

## Installation

1. Clone the repository:

```bash
git clone https://github.com/It_ba_21/safeweb-project_final
first unzip it then

For fronetnd

 cd frontend

2. Install dependencies:

npm install

3. Start the development server:
   
npm run dev

4. Open your browser at [http://localhost:5173]

   For Backend

   open new terminal
   
  1. cd backend

  2.  pip install -r requirements.txt

  3.  uvicorn main:app --reload

  4. open your browser at [https://0.0.0.0:8000]

## Usage

1. Navigate to **Scan** page to run network scans.
2. Navigate to **monitoring** page to view live host status.
3. Navigate to **Settings** to toggle theme and notifications.
4. Navigate to **Report** page to download the pdf report.
5. Navigate to **Alerts** page to show the data breach alerts.

---


## Developer
Itba Shehzadi
```
