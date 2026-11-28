# Discussion Summary – LLM Partner Collaboration & Critical Analysis

**Module:** PUSL 3205 – Large Language Models and Generative AI  
**Lab Session:** Lab 02 – AI in Everyday Challenges  

---

## 1. Collaboration Workflow with the LLM Partner
* **LLM Engine Utilized:** Claude 3.5 Sonnet / OpenAI GPT-4o conversational interfaces.
* **Prompt Engineering Strategy:**
  * Adopted a structured role-prompting approach: Instructed the model to act as a *Lead Human-Centered Product Architect* specializing in IoT edge systems and student UX.
  * Submitted the PUSL3205 Lab 2 specification for Group 1 (The Forgetful Student) along with known physical constraints of university life.
* **Iterative Refinement:**
  * *Iteration 1:* The model initially proposed a complex RFID antenna embedded into the student's backpack zipper.
  * *Critique & Re-prompting:* The group rejected this as cost-prohibitive, bulky, and unrealistic for typical undergraduates. We steered the model toward accessible Bluetooth Low Energy (BLE) micro-tags and focused the LLM's core role on contextual schedule comprehension.
  * *Iteration 2:* The model returned the refined CarryOn mobile architecture featuring dynamic checklist generation, geofenced alerts, and conversational querying.

---

## 2. Ideas Accepted vs. Ideas Discarded

| Proposed Concept | Verdict | Rationale & Critical Evaluation |
|---|:---:|---|
| Dynamic Timetable-to-Item Parsing | **Accepted** | Excellent application of LLM semantic understanding; solves the cognitive burden of manual checking. |
| BLE Micro-Tag Proximity Tracking | **Accepted** | Highly affordable, universally supported across modern smartphones, and energy-efficient. |
| Automated Backpack RFID Gate | **Discarded** | Impractical hardware burden, fragile wiring, and excessive cost for university students. |
| Cloud-Hosted Schedule Synchronization | **Modified** | Replaced with localized on-device processing to prevent academic schedule and personal location leaks. |

---

## 3. Deep-Dive Group Reflection

### A. Strengths of LLM-Assisted Product Design
The LLM accelerated the divergent thinking phase substantially. It rapidly enumerated realistic student edge cases (e.g., rain contingencies, last-minute room relocations, printed coursework submission requirements) that would have required multiple user interview sessions to surface organically.

### B. Limitations & Technical Hallucinations
Left unconstrained, LLMs tend to propose "technologically magical" features without considering physical laws or engineering constraints. For example, it initially assumed indoor BLE signal strength (RSSI) would provide exact centimeter-level coordinates through thick reinforced concrete university walls. The team had to introduce realistic probabilistic zoning (RSSI window smoothing) to overcome physical signal multipath fading.

### C. Impact on Independent Critical Thinking
Partnering with the LLM transformed our role from passive writers to active critical editors. Every feature proposed by the AI had to be justified against three strict criteria:
1. *Is the hardware affordable for a student?*
2. *Does the LLM solve a genuine problem here, or is it decorative AI?*
3. *Does this design compromise student privacy or agency?*
