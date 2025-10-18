

 SafeWeb — SAAS CyberSecurity Platform 

SafeWeb is a simple web-based network scanning tool that allows users to check the security of a website, IP address, or local network target.

It combines a React frontend with a FastAPI backend to perform quick security scans and display the results in a clean, interactive dashboard.


---

What It Does

Accepts a target IP address or domain from the user.

Sends the target to the backend server using a REST API.

The backend runs a basic nmap scan to check the most common network ports.

The scan results (open ports, services, status) are returned and displayed in the browser in a clear format.

Useful for quickly identifying exposed services on a network for security testing or learning purposes.



---

Tech Stack

Frontend: React + Vite + Tailwind CSS

Backend: FastAPI (Python)

Scanner: nmap (Fast Scan)

Other: Lucide icons, CORS enabled for frontend-backend communication



---

Features Overview

 Dashboard UI — Simple and responsive layout with navigation.

 Scan Page — Enter an IP/domain and run a fast security scan.

 Reports / Alerts / Settings Pages — Pre-structured pages for future security modules.

 Real-time Scan Output — Displays scan results directly inside the browser.



---


How It Works

1. User types a domain or IP (e.g., scanme.nmap.org) into the scan page.


2. The frontend makes a GET request to the FastAPI /scan endpoint.


3. The backend runs a quick nmap scan on the target.


4. The scan results are sent back to the frontend and displayed.



Developed by 
  Itba Shehzadi 




                                                             