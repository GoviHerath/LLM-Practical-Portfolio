# Activity Outcomes – CarryOn Product Specification

**Laboratory Session:** Lab 02 – AI in Everyday Challenges  
**Assigned Challenge:** Group 1 – The Forgetful Student  
**Product Name:** CarryOn  
**Tagline:** *Proactive campus preparedness powered by contextual intelligence.*  

---

## 1. Problem Definition & Domain Scope
University students frequently move across diverse environments throughout a single day (lecture theatres, specialized computing laboratories, libraries, and transport hubs). Each academic activity imposes dynamic equipment demands (e.g., standard laptops for lectures vs. specific development boards, printed assignment briefs, and USB drives for labs). 

Existing solutions (static alarm reminders, generic to-do apps) fail because they lack real-time context: they do not correlate *where* a student is going next with *what physical assets* are required for that specific venue and time.

---

## 2. Target User Persona
* **Primary Persona:** Undergraduate and postgraduate students balancing modular coursework, continuous assessments, and laboratory practicals.
* **Key Pain Points:**
  * Forgetting mandatory items that prevent lab participation (student ID cards, hardware adapters, lab logbooks).
  * High cognitive load caused by manually checking schedules against bag contents before leaving.
  * Misplacing personal accessories in common areas and realizing only hours later.

---

## 3. Product Architecture & Core Features
```text
┌──────────────────────────────────────────────┐
│          Student Schedule & APIs             │
│   (VLE Calendar, Deadlines, Weather Data)    │
└──────────────────────┬───────────────────────┘
                       │
                       ▼
┌──────────────────────────────────────────────┐
│           Contextual LLM Parser              │
│  - Extracts implicit physical requirements   │
│  - Generates dynamic packing checklist      │
└──────────────────────┬───────────────────────┘
                       │
                       ▼
┌──────────────────────────────────────────────┐
│       Local Proximity Engine (BLE RSSI)      │
│  - Confirmed Packed / In Proximity / Left    │
└──────────────────────┬───────────────────────┘
                       │
                       ▼
┌──────────────────────────────────────────────┐
│             Mobile App UI Triage             │
│   (Daily Checklist, Smart Alerts, Assistant) │
└──────────────────────────────────────────────┘
```
### Key Modules:
1. **Dynamic Schedule-to-Asset Parser (LLM Pipeline):**
   * Automatically ingests university timetable feeds and module briefs.
   * Employs zero-shot extraction to convert schedule descriptions (e.g., *"PUSL3205 Lab 2 Practical"*) into concrete physical requirements (*Laptop, Charger, USB Storage, Student ID*).
2. **Tri-State Proximity Monitoring:**
   * Interfaces with low-cost Bluetooth Low Energy (BLE) micro-tags attached to key belongings.
   * Classifies items into three real-time states: `Confirmed Packed` (in bag), `In Proximity` (same room), or `Missing/Not Detected`.
3. **Geofenced Departure Alerting:**
   * Utilizes smartphone accelerometer and Wi-Fi disconnect triggers to run a rapid pre-exit check before the student leaves their room, dorm, or lecture hall.
   * Triggers high-priority haptic alerts if critical academic items remain unconfirmed.
4. **Conversational Assistant ("Ask CarryOn"):**
   * Natural language interface allowing open-ended queries such as *"What do I need for tomorrow's 9 AM network session?"*
   * Automatically offers to queue items into evening packing notifications.
5. **Contextual Contingency Triggers:**
   * Connects to ambient weather and academic deadline APIs (e.g., suggests an umbrella on high rain-probability days; flags printed coursework cover sheets on submission deadlines).

---

## 4. Generative AI & LLM Implementation Details
* **Semantic Tagging:** Extracts implicit requirements that are never explicitly written in a calendar event (e.g., recognizing that an *Embedded Systems Lab* implicitly demands a calculator and safety glasses).
* **Quantized On-Device Inference:** Designed to run with small language models (SLMs) on mobile NPUs to eliminate server latency and protect student privacy.

---

## 5. Technical Feasibility & Ethical Mitigations
* **Privacy by Design:** Location coordinates and calendar feeds remain encrypted locally on the user's handset; no identifiable behavioral telemetry is sent to external cloud APIs.
* **Hardware Battery Optimization:** Employs passive BLE beacon scanning rather than continuous GPS tracking, extending micro-tag battery life up to 12 months.
* **Next Steps:** Develop an interactive front-end prototype in React Native / Flutter and benchmark parsing latency on edge devices.
