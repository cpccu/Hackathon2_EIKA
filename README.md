# 🎓 CampusOS — City University
### The All-in-One Smart Digital Campus Operating System

> **Built for CPCCU AI-Powered Web App Development & Deployment Hackathon 2026**  
> **Permanent Campus:** Khagan, Birulia, Savar, Dhaka-1340, Bangladesh (~10 km from Gabtoli)  
> **Official University Portal:** [cityuniversity.ac.bd](https://cityuniversity.ac.bd/)
>
> LIVE DEMO: https://campusoscub.vercel.app/

---

## 💡 What CampusOS Does & The Problem It Solves

City University is a vibrant, growing campus with 10+ student clubs (cultural, robotics, debate, sports, academic), multiple departments, and a dedicated shuttle bus fleet. However, vital campus information is heavily fragmented across:
- **20+ disparate Facebook groups** with unpredictable admin posting habits.
- **Messenger group chats** where urgent announcements and room changes get buried under hundreds of memes and side conversations within minutes.
- **Ad-hoc Google Forms** with no central directory of open registrations.
- **Physical notice boards** that only reach students who happen to walk past at the exact right moment.

**CampusOS** replaces this chaos with a unified, responsive, and deployable web application that serves as the single source of truth for the entire City University student body.

---

## 🏆 Real-World Usability Scenarios for a City University Student

CampusOS was engineered specifically around the day-to-day lived realities of City University students:

### 1. Scenario A: The Night Before the CSE Midterm
* **The Daily Friction:** A 2nd-year CSE student preparing for tomorrow's Data Structures midterm has to message 4 separate WhatsApp and Messenger groups asking: *"Does anyone have last year's question paper?"*
* **The CampusOS Solution:** The student opens CampusOS, navigates to the **Resource Hub**, filters by `CSE` $\to$ `3rd Semester` $\to$ `CSE-212`, and downloads the verified 2024 & 2025 Midterm Question Papers in under 10 seconds.

### 2. Scenario B: The Morning Shuttle Bus Commute
* **The Daily Friction:** A fresher living near Mirpur 10 misses their university shuttle bus because the schedule PDF was posted months ago in a buried Facebook group.
* **The CampusOS Solution:** The student checks the **Bus & Helpdesk** tab on their phone and immediately sees the Mirpur corridor departure times (07:15 AM, 08:00 AM, 09:30 AM), all intermediate stops (Mirpur 1 $\to$ Gabtoli $\to$ Birulia), driver contact details, and a live countdown to the next departure.

### 3. Scenario C: CPCCU Contest Day & Door Check-In
* **The Daily Friction:** CPCCU hosts an intra-university programming contest; 150 students register via Google Forms, creating long paper sign-in queues and lost entries at the lab entrance.
* **The CampusOS Solution:** Students click **1-Click RSVP** on CampusOS and receive a digital ticket with a unique QR code (`CU-XXXXXX`). At the door, the club executive opens the **Door Scanner** (`/admin/scanner`), points their camera at the student's phone, and marks attendance in real time.

### 4. Scenario D: Lost University ID Card in the Cafeteria
* **The Daily Friction:** A student drops their plastic ID card in the cafeteria. Their single Facebook post scrolls away unread within hours, and the finder has no central place to list it.
* **The CampusOS Solution:** The finder takes a picture on their phone, which is automatically compressed via an HTML5 canvas to ~35 KB, and posts it to the **Lost & Found** board with the tag *"Cafeteria Table 4"*. The owner searches *"ID Card"*, spots the picture, and claims it immediately.

---

## 📦 Core Modules Built (All 4 Fully Operational)

Unlike projects with static UI mockups, CampusOS features **all 4 modules working end-to-end** with real data persistence:

### 1. 📅 Module 1: Club & Event Engine (Flagship)
- Unified feed covering CPCCU, Robotics Club (CURC), Debating Club (CUDC), Cultural Club (CUCC), and Sports Club (CUSC).
- Category filtering (`Hackathon`, `Contest`, `Workshop`, `Seminar`, `Cultural Fest`, `Sports`).
- 1-Click RSVP with instant confetti celebration.
- Verifiable digital QR ticket generation in **"My Digital Passes"** (`qrcode.react`).
- Live HTML5 camera door check-in scanner (`html5-qrcode`) with manual ticket fallback for test environments.

### 2. 📚 Module 2: Centralized Academic Resource Hub (Flagship)
- Hierarchical multi-filter system:
  * **Faculty & Department:** CSE, EEE, BBA, Textile Engineering, Civil Engineering, English, Law.
  * **Semester:** 1st through 8th Semester.
  * **Material Type:** Midterm Questions, Final Questions, Lecture Slides, Lab Manuals, Handwritten Notes.
- Fast live search by course code (e.g., `CSE-111`, `CSE-212`, `MATH-141`).
- Resource submission modal supporting Google Drive, OneDrive, and direct document links.

### 3. 🚌 Module 3: Transport Navigator & Grounded Helpdesk
- Complete route directories for Mirpur 10, Uttara House Building, and Dhanmondi corridors.
- Morning Inbound and Afternoon Outbound schedules with driver phone numbers.
- Searchable accordion of official City University regulations (75% exam attendance rule, retake policies, tuition fee waivers, Orbund portal guide).
- **CampusOS AI Assistant:** Grounded AI copilot powered by Google Gemini 1.5 Flash API with local university knowledge fallback.

### 4. 🔍 Module 4: Lost Belongings & Student Grievance Box
- Post lost and found notices with **Client-Side Canvas Base64 Photo Compression** (resizes to ~35 KB JPEG; zero external cloud storage dependencies).
- Filter by status (`All`, `Lost`, `Found`, `Claimed / Reunited`).
- 1-Click *"Mark Reunited / Claimed"* resolution button.
- Official Student Grievance / Complaint Box with auto-generated tracking codes (`CU-CMP-2026-XXX`) and administrative review status indicators.

### 5. 🤖 Bonus AI Features
- **AI Notice Summarizer:** Converts long, verbose administrative notices into prioritized bullet points (Key Dates, Deadlines, Student Actions).
- **Timetable Conflict Checker:** Diagnostic tool to catch overlapping exam slots for regular and retake courses.

---

## 🛠️ Technology Stack Used

| Layer | Technologies |
| :--- | :--- |
| **Frontend Framework** | **Next.js 16.4.0** (App Router, Turbopack, React 19) |
| **Styling & Icons** | **Tailwind CSS v4**, **Lucide React** Icons |
| **Database & Persistence** | **Firebase Cloud Firestore** (Spark Plan Free Tier) + Persistent Local Fallback |
| **Authentication** | **Firebase Authentication** + 1-Click Judge Demo Accounts |
| **File & Image Engine** | **Client-Side Canvas Compressed Base64 in Firestore** (~35 KB/photo) |
| **QR Code Engine** | `qrcode.react` (Generator) + `html5-qrcode` (Live Camera Scanner) |
| **AI Integration** | **Google Gemini 1.5 Flash API** (`@google/genai`) |
| **Animation** | `canvas-confetti` |

---

## 🔑 Demo Credentials for Hackathon Judges

To ensure a seamless evaluation experience, judges can use the **1-Click Quick Login** bar directly on the screen or enter the credentials below:

| Role | Email | Password | Access / Features |
| :--- | :--- | :--- | :--- |
| **Student Demo** | `student@cityuniversity.edu.bd`<br>*(Emdadul Islam - ID: 02725105101055)* | `demo1234` | Full access: RSVP, QR passes, Resource downloads, Lost & Found |
| **CPCCU Club Lead** | `cpccu@cityuniversity.edu.bd`<br>*(Tanvir Hasan - Event Lead)* | `demo1234` | Can publish new campus events & use Door QR Scanner |
| **University Admin (DSW)** | `admin@cityuniversity.edu.bd`<br>*(Prof. Dr. Rahman M. Mahbub - DSW)* | `demo1234` | Administrative overview & grievance resolution |

---

## 🚀 How to Run the Project Locally

### Prerequisites
- **Node.js:** v18.0.0 or higher (Tested on v24.16.0)
- **npm:** v9.0.0 or higher

### Installation & Run Steps

1. **Clone the repository:**
   ```bash
   git clone https://github.com/cpccu/campusos-city-university.git
   cd campusos-city-university
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Configure Environment Variables (Optional):**
   Copy `.env.example` to `.env.local`:
   ```bash
   cp .env.example .env.local
   ```
   *(Note: The app is built with a resilient hybrid store, so it runs fully functional out-of-the-box even before adding custom Firebase keys!)*

4. **Start the development server:**
   ```bash
   npm run dev
   ```

5. **Open in browser:**
   Open [http://localhost:3000](http://localhost:3000) to view CampusOS.

6. **Production Build:**
   ```bash
   npm run build
   npm run start
   ```

---

## 🔒 Security & Credential Compliance

- In strict compliance with Section 8 & Section 14 of the Official Rulebook, **zero private API keys or database passwords are committed** to the repository.
- `.env*` files are tracked in `.gitignore`.
- Template variables are safely provided in `.env.example`.

---

## 🎬 Presentation & Demo Video Walkthrough Outline

Our 3–4 minute demo video follows the recommended judging flow:
1. **0:00 – 0:40 | Problem Statement:** The daily friction of 20+ FB groups, missed shuttle buses, and exam-night panic at City University.
2. **0:40 – 1:15 | Solution Overview:** Introducing CampusOS as the single source of truth for the Khagan campus.
3. **1:15 – 2:45 | End-to-End Live Walkthrough:**
   * Checking the Mirpur shuttle bus timetable and live countdown.
   * Filtering and downloading CSE past exam question papers.
   * 1-Click RSVP for the CPCCU Hackathon, generating the digital QR pass, and live door camera scanning.
   * Uploading a lost ID card photo using client-side canvas compression.
   * Querying the grounded AI Helpdesk about the 75% attendance rule.
4. **2:45 – 3:30 | Technical Architecture:** Next.js 16, Firebase, Base64 image compression, and Vercel deployment.
5. **3:30 – 3:45 | Impact:** Empowering City University's 10,000+ students.

---

*Developed with ❤️ for the CPCCU AI-Powered Web App Development & Deployment Hackathon 2026.*
