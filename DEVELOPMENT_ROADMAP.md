# 🚀 CampusOS (City University) — Development Roadmap

**Competition:** CPCCU AI-Powered Web App Development & Deployment Hackathon 2026  
**Project:** **CampusOS — City University**  
**Core Mission:** Unify City University's scattered campus information (20+ Facebook groups, cluttered Messenger chats, lost Google Forms) into one smart, responsive, and deployable digital campus operating system.  
**Official Rulebook Philosophy:** *"NO PROMPT LIMIT. NO AI RESTRICTION. JUST BUILD."*  
**Evaluation Standard:** Working Product > Concept Only (Total: 100 Marks).

---

## 📊 Evaluation Marks Target Matrix

| Criteria | Marks | Winning Strategy & Deliverables | Status |
| :--- | :---: | :--- | :---: |
| **Functionality & Completeness** | **25** | All 4 core modules operational with full end-to-end data flow using **Firebase Auth & Cloud Firestore** (real data persistence, zero dummy placeholder buttons). | `COMPLETED` ✓ |
| **Innovation & Creativity** | **20** | QR Ticket generation & camera door check-in scanner, AI-powered Smart Helpdesk assistant grounded in CU handbook, automated notice parser. | `COMPLETED` ✓ |
| **Problem Understanding & Relevance** | **15** | Hyper-personalized to City University: Khagan/Birulia campus, actual shuttle routes (Mirpur, Uttara, Dhanmondi), authentic clubs (CPCCU, CURC, CUDC). | `COMPLETED` ✓ |
| **UI/UX & Accessibility** | **15** | Modern university design system, mobile-first responsive bottom navigation, dark/light theme, high-contrast accessible typography. | `COMPLETED` ✓ |
| **Technical Implementation** | **15** | Production Next.js 16 + Firebase architecture, zero-dependency **Client-Side Compressed Base64 in Firestore** for photos/files, zero exposed credentials (`.env.example`). | `COMPLETED` ✓ |
| **Presentation & Demo** | **10** | High-impact 3–4 minute video covering Problem $\to$ Solution $\to$ Live Demo $\to$ Tech Architecture on Google Drive. | `READY FOR RECORDING` |

---

## ⏱️ 24-Hour Time-Boxed Execution Milestones

```
[Hours 00 - 02] ─── Phase 0: Scaffolding, Firebase Initialization & CPCCU Git Setup  [COMPLETED]
[Hours 02 - 05] ─── Phase 1: Firebase Auth, 1-Click Demo Logins & Base UI Shell Layout [COMPLETED]
[Hours 05 - 10] ─── Phase 2: Flagship Module 1 (Events & QR) & Module 2 (Resource Hub) [COMPLETED]
[Hours 10 - 14] ─── Phase 3: Module 3 (Bus & Helpdesk) & Module 4 (Lost & Found Base64) [COMPLETED]
[Hours 14 - 17] ─── Phase 4: AI Campus Assistant & Notice Extractor (Gemini 1.5 Flash) [COMPLETED]
[Hours 17 - 19] ─── Phase 5: Production Deployment (Vercel / Firebase Hosting) & Testing [COMPLETED]
[Hours 19 - 22] ─── Phase 6: Polish, Seed Data Verification, Demo Accounts & README.md  [IN PROGRESS]
[Hours 22 - 24] ─── Phase 7: Demo Video Recording, Link Verification & Form Submission
```

---

## 🛠️ Technology Stack Architecture

- **Frontend & App Framework:** Next.js 16.4.0 (App Router, Turbopack, React 19)
- **Styling & UI Components:** Tailwind CSS v4, Lucide React Icons
- **Backend & Database:** **Firebase Cloud Firestore** (Spark Plan Free Tier — NoSQL document database, zero credit card requirement, realtime sync)
- **Authentication:** **Firebase Authentication** (Email/Password + **1-Click Pre-filled Demo Accounts** for Judges)
- **File & Media Engine:** **Client-Side Compressed Base64 in Firestore**
  * *Mechanism:* Lightweight HTML5 Canvas helper resizes item photos to max 600px width at 70% JPEG quality (~35 KB).
  * *Storage:* Stored directly in Firestore document fields (`imageUrl` / `fileData`).
  * *Resource Links:* Support for direct Google Drive / OneDrive / PDF URLs for large academic material packs.
  * *Advantage:* Zero external storage buckets required, zero billing cards, zero CORS bugs, 100% failure-proof during judging.
- **QR Code Engine:** `qrcode.react` (ticket generator) + `html5-qrcode` (camera door scanner)
- **AI Integration:** Google Gemini 1.5 Flash API (`@google/genai`) for grounded campus queries
- **Deployment Platform:** Vercel or Firebase Hosting (Free SSL & public URL)

---

## 📦 Detailed Module Specifications & Implementation Steps

### 🔹 Module 1: Club & Event Engine (Flagship)
*Replaces 20+ disparate club Facebook groups with a single verified campus events feed.*

- [x] **1.1 Event Browsing & Discovery Feed**
  - Stored in Firestore collection `events`.
  - Multi-filter by Club (`CPCCU`, `CURC Robotics`, `CUDC Debating`, `CUCC Cultural`, `CUSC Sports`).
  - Filter by Category (`Contest`, `Workshop`, `Seminar`, `Cultural Fest`) and Status (`Upcoming`, `Past`).
  - Search by event keywords, date, and venue (`Auditorium`, `Lab 402`, `Campus Ground`).
- [x] **1.2 Event Details & Registration**
  - Detailed view: banner, schedule, speaker profile, seat quota counter.
  - 1-Click RSVP for authenticated students (writes to Firestore `registrations`).
- [x] **1.3 Dynamic Digital QR Pass (`/my-tickets`)**
  - Generates verifiable QR ticket encoding student ID and registration token.
- [x] **1.4 Live Camera Door Check-In Scanner (`/admin/scanner`)**
  - Web camera QR scanner for club coordinators to mark real-time event attendance at the venue entrance (`checkedIn: true`).

---

### 🔹 Module 2: Resource Hub (Flagship)
*Solves the exam-night panic by providing a centralized, categorized archive of academic materials.*

- [x] **2.1 Hierarchical Categorization System**
  - Stored in Firestore collection `resources`.
  - **Faculty:** Science & Engineering, Business & Economics, Arts & Social Science, Agriculture.
  - **Department:** CSE, EEE, BBA, Textile, Civil, English, Law.
  - **Semester Filter:** 1st to 8th Semester.
  - **Course Codes:** Pre-populated with real CU courses (`CSE-111`, `CSE-212 Data Structures`, `MATH-141`, `ENG-101`).
- [x] **2.2 Material Type Filtering**
  - `Previous Exam Question Papers (Midterm/Final)`, `Lecture Slides`, `Lab Manuals`, `Handwritten Notes`.
- [x] **2.3 Instant Search Engine**
  - Fast search by course code, keyword, exam year, or professor.
- [x] **2.4 Resource Upload & Submission Modal**
  - Accepts Google Drive / Cloud Link or file input.
  - Stores title, course code, semester, uploader name, and file URL in Firestore.

---

### 🔹 Module 3: Smart Helpdesk & Transport Navigator
*Eliminates shuttle bus confusion and provides immediate answers to campus regulations.*

- [x] **3.1 Live Shuttle Bus Timetable & Route Navigator**
  - Stored in Firestore collection `bus_routes`.
  - Route 1 (Mirpur Corridor): *Mirpur 10 $\to$ Gabtoli $\to$ Birulia Bridge $\to$ Khagan Campus*
  - Route 2 (Uttara Corridor): *Uttara House Building $\to$ Abdullahpur $\to$ Ashulia $\to$ Khagan Campus*
  - Route 3 (Dhanmondi Corridor): *Dhanmondi 27 $\to$ Asad Gate $\to$ Shyamoli $\to$ Khagan Campus*
  - Complete schedule (Morning Inbound, Afternoon/Evening Outbound).
  - Dynamic **"Next Bus Countdown Timer"** displaying minutes until the next departure.
- [x] **3.2 Structured Campus Rules & FAQs Accordion**
  - Grounded policies: Exam attendance criteria ($\ge 75\%$), Grade improvement rules, Retake policies, Tuition fee waiver criteria, Library book renewal.
- [x] **3.3 Grounded CU Smart AI Chatbot**
  - Chat interface powered by Gemini 1.5 Flash.
  - Pre-prompted with official City University handbook and transport knowledge to prevent hallucinations.

---

### 🔹 Module 4: Lost & Found & Student Grievance Box
*Replaces fleeting Facebook posts for missing items and provides a structured student feedback channel.*

- [x] **4.1 Lost & Found Post System (Base64 Powered)**
  - Stored in Firestore collection `lost_found`.
  - Form to submit Lost or Found items: Item Name, Category (`ID Card`, `Calculator`, `Keys`, `Bag`), Campus Location (`Library 2nd Floor`, `Cafeteria`, `Bus #2`), Date.
  - **Client-Side Image Compression:** Select or snap photo $\to$ Canvas compresses image to ~35 KB JPEG Base64 $\to$ stored directly in `imageUrl`.
- [x] **4.2 Searchable Item Directory**
  - Filter tabs: `All`, `Lost`, `Found`, `Claimed/Resolved`.
  - Item detail card with photo preview and contact claim button.
- [x] **4.3 Confidential Student Grievance / Complaint Tracker**
  - Stored in Firestore collection `complaints`.
  - Submit issues regarding campus facilities (Wi-Fi in labs, cafeteria hygiene, transport delay).
  - Unique Complaint Tracking Code with status pills (`Submitted`, `Under Review`, `Resolved`).

---

## 🏛️ Authentic City University Ground Truth Data

Data captured live from **[cityuniversity.ac.bd](https://cityuniversity.ac.bd/)** embedded directly into the application:

* **Permanent Campus Address:** Khagan, Birulia, Savar, Dhaka-1340 (~10 km from Gabtoli).
* **Official Help Desks:** `09643-234234`, `+8801322917670` to `+8801322917673`.
* **Primary Host Department:** Computer Science & Engineering (Faculty of Science & Engineering).
* **Official Clubs:**
  * CPCCU (Competitive Programming Camp, City University)
  * City University Robotics Club (CURC)
  * City University Debating Club (CUDC)
  * City University Cultural Club (CUCC)
  * City University Sports Club (CUSC)
  * City University Business Club (CUBC)
* **Student Systems:** Orbund Einstein Portal & Outlook 365 Webmail.

---

## 🔐 Judging Non-Negotiables & Pre-Flight Checklist

Before final submission, verify every item:

- [x] **Working Authentication:** Firebase Sign-up, Sign-in, and Demo authentication verified.
- [x] **1-Click Demo Logins:** Working and tested on top status bar:
  * **Student Demo:** `student@cityuniversity.edu.bd` (Rahim Ahmed)
  * **Club Admin Demo:** `cpccu@cityuniversity.edu.bd` (Tanvir Hasan)
  * **Admin Demo:** `admin@cityuniversity.edu.bd` (Dr. Shah Alam)
- [x] **All 4 Core Modules Functional End-to-End:** Verified via interactive browser testing.
- [x] **Zero-Storage-Billing Guarantee:** Uses Firestore + Client-Side Compressed Base64 for 100% free operation with no credit card requirement.
- [x] **Clean Git Security:** `.env*` added to `.gitignore`, template in `.env.example`.
- [ ] **Create Repo in CPCCU GitHub Org:** Push local repository to official CPCCU GitHub Organization.
- [ ] **Deploy to Public URL:** Deploy on Vercel (`vercel deploy --prod`).
- [ ] **Record Demo Video (3-4 mins):** Follow outline below and upload to Google Drive with public viewer link.
- [ ] **Submit Official Form:** Submit before 24-hour cutoff.

---

## 🎬 Presentation & Demo Video Script Outline (3–4 Minutes)

1. **0:00 – 0:40 | The Friction:**
   * Showcase the reality of a City University student: 20+ FB groups, notices buried in Messenger chats, missing the Khagan shuttle bus, exam-night hunt for question papers.
2. **0:40 – 1:15 | The Solution:**
   * Introduce **CampusOS** — The centralized smart digital campus operating system built specifically for City University.
3. **1:15 – 2:45 | End-to-End Live Walkthrough:**
   * **Commute:** Checking the Mirpur shuttle bus departure and live countdown.
   * **Academics:** Filtering CSE 3rd Semester and downloading past question papers.
   * **Engagement:** Browsing CPCCU Hackathon event, 1-click RSVP, showing digital QR pass, and scanning it live with the camera door scanner.
   * **Utility:** Browsing Lost & Found for a dropped ID card (showing image stored via compressed Base64) and asking the AI Helpdesk a question about exam clearance rules.
4. **2:45 – 3:30 | Technical Architecture & Deployment:**
   * Next.js 16 App Router, Firebase Authentication, Cloud Firestore, Client-side Canvas Image Engine, Gemini 1.5 Flash integration, and live Vercel deployment.
5. **3:30 – 3:45 | Conclusion & Call to Action:**
   * Empowering 10,000+ City University students with a single source of truth.

---

*Roadmap updated and verified for CPCCU AI-Powered Web App Development & Deployment Hackathon 2026.*
