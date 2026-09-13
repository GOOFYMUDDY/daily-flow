# Daily Flow 🧠⚡

> A personalised, energy-aware scheduler that helps university students beat burnout — by learning not just *when* they're free, but *when they actually work best*.

**Team Mozzarella Cheese**
🎥 [Video Presentation](https://youtu.be/nS2Qrj4OfH8) · 🎨 [Presentation Slides](https://canva.link/0s7rtmd00eifxyf) · 🖥️ [Prototype link](https://jin-0804.github.io/daily-flow/)

---

## 📌 Problem Statement

**Track:** Stress & Workload Manager — *Beating the Burnout*

Students juggle classes, assignments, work, social activities, errands, and personal needs. When everything piles up, they struggle to prioritise, delay difficult tasks, and end up cramming or sacrificing rest.

Existing schedulers (**Motion, Reclaim, Sunsama**) only look at time, deadlines, priorities, and availability. They can tell you which slots are *free*, but they cannot tell which free slot is *best* for you. They fail to account for the personal conditions that decide where a task should actually go.

**Where they fail:** Being *available* ≠ being *able to do the task*. A slot can look perfect by time and energy, yet still be wrong because of personal context.

**Example:** A student wants to study Chemistry at 10 PM.  
- **Existing tools:** "10 PM is free, no deadline conflict → schedule it."  
- **Student's reality:** "I can only focus on Chemistry with my friend."  
- **Result:** Friend is asleep, task won't get done well.  
Existing tools would still schedule it — they never learned that condition.

**Our answer:** Daily Flow learns the student's energy, experiences, and personal context to recommend times that actually work for them.

---

## 💡 Our Solution

Two complementary layers working together:

| Layer | Role | Question it answers |
|---|---|---|
| **Deterministic Energy Layer** | Tracks mental / physical / social energy before & after activities; filters suitable slots via fixed rules | *Which times are suitable?* |
| **Personalisation Layer (AI)** | Uses reflections, conversations, preferences & past experiences to pick the best fit and explain why | *Which suitable time is best for this student?* |

---

## ✨ Feature Set

1. **Smart Schedule & Workload Management** — Manage tasks, events, deadlines, recurring activities; detect overload and suggest breaks/recovery/adjustments.
2. **Personalised Scheduling** — Recommend the best slot from suitable options, *with an explanation*.
3. **Personalised AI Agent** — Discuss tasks, difficulties, and preferences; learns from conversations to improve future recommendations.
4. **Energy Tracking** — Mental, physical, and social energy tracked before/after activities as the deterministic filtering basis.
5. **Reflection & Feedback** — Capture *how* and *why* an activity affected the student; feeds continuous personalisation.

---

## 🧭 Ideation & Process

### Ideas Kept
- **3-Dimension Energy Tracking** — more accurate than a single vague stress score
- **Personalised AI Scheduling** — selects best slot from suitable options
- **Personalised AI Agent** — understands the student beyond their schedule
- **Post-Event Reflection** — captures the *why* behind the numbers
- **Free Time as Recovery** — empty periods are learned recovery events too
- **Activity Categories / Tags** — learn patterns by category (e.g. `[Revision]`), not per task name
- **Task Splitting** — break large tasks into manageable sessions
- **Mascot-Based AI Agent** — engaging, approachable (penguin 🐧)

### Ideas Dropped
| Idea | Reason |
|---|---|
| Single Stress Level Tracking | Too vague; can't distinguish load types |
| Full AI-Based Scheduling | Too undetermined; energy layer stays deterministic |
| Plain To-Do List w/ Priority Tags | Already done by Todoist/Notion; no load insight |
| Fixed Scheduling Rules | Can't adapt to individual differences |

### Mentor Consultation
**8/9/2026 — Zach Khong:** *Focus more on personalisation by collecting text-based reflections, AI agent conversations, and context shared during planning.*

→ **Changed:** Expanded beyond energy levels to a personalised context layer. Energy identifies *suitable* slots; the AI agent uses learned context to pick the *best-fit* slot. Past experiences also feed task-splitting and future recommendations.

Our combined idea into final protoype:[Ideation Board](https://github.com/Jin-0804/daily-flow/blob/5c06dfb38a2d92905cc30c7392a085c7689c07d7/idea.drawio%20(1).png)

---

## 🗺️ Core System Design

### 1. Two Event Types
- **Fixed Events** — predictable/recurring: classes, badminton training, sleep, medication. Auto-appear on future dates via recurrence rules.
- **Temporary Events** — to be scheduled: study chapter, finish assignment, gym, games.

### 2. Every Activity Has a Demand (1–10 scale)

🧠 **Mental** · 💪 **Physical** · 👥 **Social**

Students give **Before / After** feedback. Example — Math Lecture:

| | Mental | Physical | Social |
|---|---|---|---|
| Before | 8 | 6 | 7 |
| After | 6 | 8 | 6 |
| **Change** | **−2** | **+2** | **−1** |

The system learns which events **drain** and which **restore** — including free time, treated as an *empty recovery event*.

**Reducing feedback burden:** only ~3 initial feedback requests per activity type; once estimates stabilise, requests become occasional confirmations (*"Do you feel 😐 right now, or different?"*).

### 3. Scheduling Logic

When adding e.g. *"Study math notes chapter 1, 30 mins"*, the system evaluates all free periods:

| Time | Predicted Mental | Physical | Social | Verdict |
|---|---|---|---|---|
| 10–11 AM | 4 | 6 | 3 | ✕ Not suitable |
| 2–3 PM | 7 | 5 | 7 | ✓ Suitable |
| 6–7 PM | 5 | 8 | 8 | ✕ |
| 8–9 PM | 6 | 8 | 8 | ✕ |

**Suitability rules:** required dimension **≥ 7/10**, all others **≥ 5/10**.

- **Scenario 1:** 2 PM chosen → Mental 7 ✓ passes
- **Scenario 2:** 10 AM chosen → Mental 4 ✕ rejected
- **Scenario 3:** 10:30 AM chosen → recalculate state after the 10:00–10:30 recovery period, *then* check

If a student insists on an unsuitable slot, a **warning** is shown — never a hard block.

### 4. Personalised Reasoning (AI Layer)

The energy table above only tells us *which slots are suitable*. It does **not** tell us *which suitable slot is best for this student*. That's the AI layer's job.

**Step 1 — Deterministic filter**  
Energy rules produce a shortlist of suitable slots.  
→ 2–3 PM ✓ · 6–7 PM ✓ · 8–9 PM ✓

**Step 2 — Personalised reasoning**  
The AI agent takes that shortlist and combines it with learned personal context:

- **Post-event reflections** — *"I lose focus on Chemistry after 30 mins alone."*
- **Agent conversations** — *"I prefer studying with my friend."*
- **Preferences & past outcomes** — *"Group study works, solo late-night doesn't."*
- **Structured personal memory** — stored facts, not just chat history.

**Step 3 — Best-fit recommendation + explanation**  
The agent picks the best slot from the shortlist and explains *why*:

> *"2–3 PM is best — you usually focus better on Chemistry with your friend, and they're free then."*

**Deterministic layer:** *Which times are suitable?*  
**Personalisation layer:** *Which suitable time is best for this student?*

---

## 🖥️ Prototype (This Repo)

A working mobile-style front-end prototype (`index.html` + modular JS):

| Screen | What it does |
|---|---|
| **Today / Dashboard** | Energy Capacity card (Mental / Physical / Social), optimal focus window, daily task list with tap-to-complete, reflection prompts |
| **Agent** | Chat with the AI study companion — plan focus sprints, explain concepts, quick-prompt chips |
| **Calendar** | **Day** (color-coded timeline), **Week** (days left, hours across top, scrollable, green/red energy), **Month** (dots = tasks) |
| **Add Task** | Bottom sheet: title, category (Focus / Lecture / Recovery / Sport), duration, location → drops into **placement mode** |
| **Placement Mode** | Auto-suggests a green (high-energy) slot; drag/tap to move; 🟢 high · 🟡 medium · 🔴 low energy zones; Confirm or Cancel; ask the agent for the best slot |
| **Capacity Check-In** | Sliders for mental / physical / social state; agent pop-out to share how the event went; **Save & Recalibrate** auto-adjusts afternoon blocks |
| **Reflection** | Post-event modal with quick tags + free text, saved back to task/calendar event |
| **Profile** | User info, chronobiology baseline (Early Peak · Lion), wearable sync (Apple Watch, Oura), settings |

### File Structure
```
index.html          → Phone frame, all screens, modals
css/style.css       → Animations, screen/view transitions
js/app.js           → Screen switching, bottom dock, toasts, task completion
js/calendar.js      → Month/Week/Day rendering, placement mode, capacity & reflection logic
js/agent.js         → Agent chat, mock replies, typing indicator
js/datetime.js      → Live clock, dynamic today/tomorrow events, dynamic schedule
images/             → agent-penguin.png
```

---

## 🔍 What Makes It Different

| Feature | Motion | Reclaim | Sunsama | **Our System** |
|---|---|---|---|---|
| Task & Calendar Scheduling | ✓ | ✓ | ✓ | ✓ |
| Priorities & Deadlines | ✓ | ✓ | ✓ | ✓ |
| Automatic Rescheduling | ✓ | ✓ | ✓ | ✓ |
| Workload Management | ✓ | ✓ | ✓ | ✓ |
| Mental / Physical / Social Energy Learning | — | — | — | **✓** |
| Personal Context from Reflections & Conversations | — | Limited | — | **✓** |
| Personalised Best-Slot Recommendation | ✓ | ✓ | ✓ | **✓ + personal context** |
| Learns from Past Experiences | Limited | ✓ | Limited | **✓** |

**Key differentiators:**
- 🎯 **Personalised time-slot recommendation** — energy finds *suitable*; context finds *best*
- 📝 **Learning from text reflections** — the *why* behind the numbers
- 🤖 **Personalised AI agent** — learns habits, preferences, and context from conversation
- 🔄 **Continuous personalisation** — the more you use it, the better it knows you
- ✂️ **Context-aware task splitting** — past struggles → smaller suggested sessions
- 🧩 **Energy + personal context** — deterministic layer + AI personalisation layer

---

## 🏗️ Technical Architecture & Feasibility

### Tech Stack

| Component | Technology | Purpose / Why |
|---|---|---|
| **Mobile Frontend** | React Native | Familiar JS/TS workflow; expandable to web later. *Constraint:* some platform-specific behaviour needed for iOS/Android |
| **Backend** | Bun | Fast, lightweight runtime for APIs, energy calculations, scheduling logic |
| **Database** | PostgreSQL + Prisma | Reliable self-hostable relational DB; type-safe SDK |
| **Authentication** | OAuth | Secure sign-in without storing passwords |
| **AI Agent** | OpenAI API + LangGraph | LLM capability + multi-step workflows for context retrieval, reasoning, recommendations. *Constraint:* cost, latency, rate limits, response inconsistency → keep constraints deterministic |
| **Scheduling & Workflows** | Temporal | Reliable execution of recurring events, delayed tasks, reminders, background jobs; survives restarts. *Constraint:* added infra complexity |
| **Hosting** | DigitalOcean | Straightforward cloud env; supports self-hosted PostgreSQL + Temporal |
| **Containerisation** | Docker | Consistent packaging & deployment |

### Build Plan & Scope

**5.3.1 Core System** — Deterministic Energy Layer + Personalisation Layer

**5.3.2 Student Schedule** — Fixed Events (recurring) & Temporary Events (to schedule)

**5.3.3 Deterministic Energy Layer**
- 3 dimensions on a 1–10 scale
- Before/After feedback → observed change per activity
- Learns drains *and* restores (free time = recovery activity)
- **Activity categories/tags** avoid per-task feedback spam
- Feedback frequency tapers as estimates stabilise

**5.3.5 Predicting Suitable Time Slots**
- Calculate predicted energy state at each candidate start time
- Apply rules: required dim ≥ 7/10, others ≥ 5/10
- **Recalculate within a slot** (e.g. 10:00–10:30 free recovery *before* 10:30 task)
- Warn, don't block, on unsuitable choices

**5.3.7 Personalised AI Agent**
- Sits on top of the deterministic layer, receives structured suitability results
- Learns from reflections, conversations, planning discussions, preferences, past outcomes
- Acts as the system interface — can create, edit, and reschedule events via APIs
- *Example:* "You usually focus better on Chemistry with your friend, who's free around 2 PM" → 2 PM = best fit

**5.3.8 Structured Personal Memory**
- Important info stored as **structured context**, not just chat history
- e.g. *Preference: prefers studying Chemistry with a friend* · *Pattern: concentration drops late at night*
- Conversation history → conversational context · Personal context → retained for future use

**5.3.9 Task Breakdown**
- Agent uses past experience to split difficult tasks (e.g. a 3-hour Biology assignment that previously caused focus loss → 3 × 1-hour sessions placed in suitable windows)

---

## 🚀 Running the Prototype

No build step required — it's a static front-end prototype.

```bash
# Clone
git clone <repo-url>
cd daily-flow

# Serve locally (any static server)
python3 -m http.server 8000
# or
npx serve .
```

Then open `http://localhost:8000` in your browser.
