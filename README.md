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

## 2.0 Ideation & Process

### 2.1 Ideas We Considered

| Idea | Decision & Reason |
|---|---|
| **3-Dimension Energy Tracking** | **Kept** — Tracks mental, physical, and social energy before and after activities. This provides a more accurate and deterministic basis for filtering suitable time slots. |
| **Personalised AI Scheduling** | **Kept** — Uses the student's personal preferences, experiences, and context to select the best time slot from the suitable options. |
| **Personalised AI Agent** | **Kept** — Allows students to discuss their tasks, difficulties, preferences, and personal context, helping the system understand the student beyond their schedule and improve future recommendations. |
| **Post-Event Reflection** | **Kept** — Captures what happened and why an activity affected the student, providing additional context for personalisation. |
| **Free Time as Recovery** | **Kept** — Treats free time as a recovery period and learns how different amounts of free time affect the student's energy. |
| **Activity Categories / Tags** | **Kept** — Groups similar activities so the system can learn from shared patterns instead of treating every individual task as completely new. |
| **Task Splitting** | **Kept** — Allows large tasks to be broken into smaller sessions when this better suits the student's workload and personal preferences. |
| **Mascot-Based Character AI Agent** | **Kept** — Considered to make the personalised AI agent more engaging and approachable. |
| **Single Stress Level Tracking** | **Dropped** — A single stress score is too vague and does not distinguish between different types of load. It was replaced with mental, physical, and social energy levels. |
| **Full AI-Based Scheduling** | **Dropped** — Relying entirely on AI to determine suitable time slots is too undetermined. Instead, energy levels provide a deterministic filtering layer, while AI handles personalised recommendations. |
| **Plain Workload To-Do List with Priority Tags** | **Dropped** — Similar to existing tools such as Todoist and Notion. It mainly manages tasks and priorities without helping students understand their mental, physical, and social load. |
| **Fixed Scheduling Rules** | **Dropped** — Fixed rules cannot sufficiently adapt to differences in students' preferences, experiences, and responses to activities. |

### 2.2 Ideation Boards

#### Idea 1

The Stress & Workload Manager ("Beating the Burnout" track) aims to prevent university students from reaching burnout by visualizing their total load across mental, physical, social, time, and errand categories. Rather than acting purely as a passive tracker, the application actively balances task loads, postpones low-priority items, and suggests recovery actions like sleep or social activities.

**Key Features & UI Concept**
- **Calendar & Integration:** Integrates with Google Classroom and team platforms to automatically prompt users to add assignment and project deadlines. Users manually plot tasks across categories including academics, work, revision, social, and personal time.
- **AI Capacity & Overload Prevention:** An AI engine calculates daily, weekly, and monthly capacity levels. It alerts users when stress limits are exceeded and provides real-time workload recommendations during the planning phase.
- **Date Selection & Categorization:** Supports single-click or long-press multi-date task planning. Users can tag plans under specific categories (e.g., exercise, study, social), which display visual icons on calendar dates.
- **Health Tracking & Task Status:** Syncs with smartwatches to track sleep patterns and monitor physical strain. Detailed daily task views feature time windows (e.g., 12 PM - 3 PM), status tracking ("Finished early" or "Finished late"), and direct options to edit or delete entries alongside a dedicated To-Do list view.

#### Idea 2

**Core Mission:** The project is an AI-powered lifestyle app built to prevent university student burnout by managing total workload capacity across mental, physical, time, errand, and social dimensions. Instead of just tracking stress passively, it actively balances schedules, postpones low-priority items, and pushes recovery prompts.

**Key System Functions**
- **Smart Calendar & Categorization:** Integrates with tools like Google Classroom to import tasks. It categorizes schedules into Fixed Events (recurring routines like classes and training) and Temporary Tasks (assignments, gym, study).
- **Capacity & Demand Tracking:** Measures student energy on a 1–10 scale across Mental, Physical, and Social capacities. The system tracks how specific tasks drain energy—or how unstructured free time restores it—using simple "Before/After" feedback logs.
- **Smart Scheduling Engine:** Evaluates optimal times to place new tasks. It recommends slots where the required capacity is high (≥ 7/10) and other stats remain healthy (≥ 4/10). If a task is scheduled during low energy, the system recalculates recovery or triggers an overload warning.
- **Health Watch Sync & Task Logging:** Syncs with smartwatches to monitor sleep schedules, provides task status updates ("Finished early/late"), and relies on category tags (e.g., [Revision]) to avoid asking for repetitive user feedback.

#### Overview of Core System Design

**1. Categorize every event into 2 types.**

**Fixed Events** — Events that usually happen at predictable times.
- Classes
- Badminton training
- Sleep
- Medication

**Temporary Events**
- Study Chapter 1
- Finish assignment section
- Complete mathematics tutorial work
- Go to the gym
- Play games

| Time | Event |
|---|---|
| 8–10 AM | Class |
| 10–11 AM | Free |
| 11–1 PM | Class |
| 1–2 PM | Lunch |
| 2–4 PM | Free |
| 4–6 PM | Badminton |
| 6–8 PM | Free |

*Student adds all events into calendar. Recurring events (aka fixed events) automatically appear on future days.*

**2. Every activity has a demand.**

System describes an activity using three main dimensions:

- 🧠 **Mental** — How much concentration/thinking it requires.
- 💪 **Physical** — How much physical energy it requires.
- 👥 **Social** — How much social energy it requires.

We score the capacity as 1 to 10. We ask student for feedback Before and After an event.

**How are you feeling?**

| Dimension | Emoji Scale |
|---|---|
| 🧠 Mental | 😫 1 · 😕 3 · 😐 5 · 🙂 7 · 😄 10 |
| 💪 Physical | 😫 1 · 😕 3 · 😐 5 · 🙂 7 · 😄 10 |
| 👥 Social | 😫 1 · 😕 3 · 😐 5 · 🙂 7 · 😄 10 |

Or use slider: 😫 ───────────── 😊 (7)

Based on provided feedback, system tracks each type of event's demand. For example, attending a Math Lecture Class:

| | Mental | Physical | Social |
|---|---|---|---|
| Before | 8 | 9 | 7 |
| After | 6 | 8 | 6 |
| **Change** | **−2** | **−1** | **−1** |

The system understands both: Which event drains the student? And which event helps the student recover?

- If there is an empty event (e.g., '6–8 PM Free'), the system will track how much the student recovers with this amount of empty free time doing nothing. This is stored as an **Empty event** (aka 'doing nothing' as a recovery event too).

The system only asks user for feedback 3 times initially. If the system finds a good average on every feedback, it would stop asking (or use a confirmation method like *"Do you feel 😐 right now? or do you feel different?"*) so the user doesn't get annoyed with frequent feedback requests.

The system keeps collecting feedback and finds the average demand or recovery each event gives regularly to keep updated.

**3. Scheduling**

When student wants to add a new event — example: *'Study math notes chapter_1 30 mins'* — the app looks at all possible free periods.

For example:
- 10–11 AM Free
- 2–3 PM Free
- 6–7 PM Free
- 8–9 PM Free

But which to choose? It will calculate the current state of the student, after a series of events for each time frame.

| Time | Mental | Physical | Social |
|---|---|---|---|
| 10–11 AM Free | 4 | 6 | 3 |
| 2–3 PM Free | 7 | 5 | 7 |
| 6–7 PM Free | 5 | 8 | 8 |
| 8–9 PM Free | 6 | 8 | 8 |

But we need to consider which is the ideal ratio. Using 7/10 as standard, if the ratio we are looking at is ≥ 7/10 we suggest the user place the event there. While other capacities must be minimum 4/10, for good balance.

**Scenario 1:** User chose '2PM - 2:30 PM' and based on our event *'Study math notes chapter_1 30 mins'*, this would drain "Mental Capacity". So we check if Mental capacity during that time is ≥7/10, and other capacities are ≥5/10. In this case it satisfied, so it is a good choice for user to pick there.

**Scenario 2:** User wants to choose '10AM - 10:30AM'. But according to the table, '10–11 AM Free 4 6 3' — Mental capacity is 4/10, less than 7/10. So we would not suggest placing there.

**Scenario 3:** User wants to choose '10:30AM - 11AM'. This time, the current state must be recalculated, because there is an 'Empty event' during 10AM - 10:30AM. This is a recovery event, so the student stats should be recalculated. Then only check if it satisfies the Capacity ratio.

If it didn't satisfy yet and the student wants to place it there, a **Warning** will be given.

**4. Problem that might occur:**

Every event is treated independently and tracked independently based on exact name — example: 'Revision Math Chapter_1' and 'Revision Math Chapter_2'. Both are similar things but naming different causes 2 events to be tracked and ask feedback separately, which might annoy the user.

**Solution:** Add a categorizing tagging system. Example: student can add tag `[revision]`, so event is tracked based on category. In the future, if student adds a new event 'Revision Chemistry Chapter_9' `[Revision]`, the system will know to use `[Revision]` type demand capacity to evaluate.

#### Prototype 1

**Daily Check-in & Stress Management**
- Tracks check-in streaks and logs how users are managing their day.
- Measures overall mood using expressive emoji indicators.
- Adjusts load dimensions (Academic, Social, Personal) using interactive sliders.

**Schedule & Timeline Management**
- Warns users about high cognitive load peaks and provides options to adjust tasks.
- Organizes daily timelines with time-blocked events such as lectures, focus work, resting spaces, and social study groups.

**Rebalance & Workload Projection**
- Displays a comparative load projection (e.g., reducing current load from 85% to a projected 55%).
- Categorizes tasks by priority and type (Academic, Mental) and features an "Auto-defer low priority tasks" function to restore balance.

**Accessibility & Settings**
- Customizes vision and display preferences, including adjustable app-wide text sizing.
- Offers a High Contrast Mode toggle for enhanced readability.
- Includes a Color-blind Palette selector to optimize color schemes for specific vision types.

#### Idea 4

**Dashboard**
- Tracks overall energy levels and provides real-time motivational encouragement from a virtual companion.
- Displays a comprehensive workload overview tracking mental, physical, and social load alongside task completion percentages.
- Provides a direct shortcut to initiate AI-assisted scheduling.

**Calendar**
- Features a monthly energy forecast with a color-coded grid mapping out low, medium, and high demand days.
- Generates automated energy warnings and recommendations to reschedule non-essential tasks and prevent burnout.
- Includes an option to view detailed daily agendas.

**Pet ("Baobei's Home")**
- Features an interactive virtual pet with real-time status bars tracking growth, hunger, and energy levels.
- Allows users to feed the pet using collected berries.
- Rewards consistency and task completion by earning berries and crystals to help the pet grow.

**AI Schedule**
- Generates smart recommendations for meals, naps, tasks, and routines.
- Provides nutritional details (such as calories and protein content) for suggested meal plans with options to accept, edit, or dismiss recommendations.

**Workload Analytics**
- Visualizes energy distribution across multiple dimensions (Mental, Physical, Social, Time, Creative, and Emotional) using a radar chart.
- Delivers AI-driven recovery suggestions based on current burnout levels, such as scheduling quiet time when social energy is depleted.

#### Idea 5

**Bio-Adaptive Scheduling & Smart Slotted Planning**
- Dynamically organizes academic schedules, lectures, and assignments by matching them with the user's optimal cognitive windows.
- Automatically populates "smart slotted" focus sprints alongside designated recovery breaks and outdoor mindfulness walks to maximize productivity without burnout.

**Circadian Energy Analytics & Rhythm Tracking**
- Features an interactive "Estimated Energy Curve" graph mapping 24-hour fluctuations in peak flow, steady states, and rest periods.
- Monitors real-time alertness percentages, calculates remaining optimal focus hours, and flags predicted mental slumps to prompt timely recharges.

**Wearable Synchronization & Biometric Monitoring**
- Integrates seamlessly with health trackers like Apple Watch and Oura Ring to pull continuous metrics including sleep scores, heart rate variability (HRV), and bio-sensors.
- Calculates a comprehensive multi-dimensional "Energy Capacity" score separating metrics into Mental Focus, Physical Vitality, and Social Battery on a 10-point scale.

**Interactive Capacity Check-Ins & Auto-Recalibration**
- Provides a manual "Capacity Check-In" interface with sliders to gauge real-time states from foggy to peak flow, or drained to energized.
- Offers a "Save & Recalibrate Rhythm" function that instantly auto-adjusts upcoming afternoon study blocks based on current physiological feedback.

**Comprehensive Multi-View Calendar**
- Offers monthly snapshot calendars with status indicator dots and granular weekly hourly timetables color-coded by event category (fixed university lectures, revision sessions, gym time).
- Consolidates external collaboration tools, seamlessly blending video conferencing applications like Zoom calls and Google Meet sessions into daily student workflows.

**Profile & Chronobiology Configuration**
- Houses academic profile settings including degree program specifics (e.g., Cognitive Science & Physics), student names, and university calendar synchronizations.
- Customizes chronobiology baselines (such as "Early Peak - Lion") and manages automated notification triggers and biometric tracking preferences.

#### Idea 6

**Dashboard**
- Displays a cumulative load summary with cognitive fatigue tracking, max peak, drain rate, and reserve time.
- Detects cognitive bottlenecks and offers options to schedule recovery breaks or adjust tasks.
- Tracks load dimensions such as Mental Load, Time Pressure, Physical Strain, Social Interaction, and Errands & Admin.
- Shows current and upcoming activities with real-time progress and drain indicators.

**Calendar & Timeline**
- Features a day/schedule view mapping out fixed events, recovery times, free time, smart slotted assignments, and breaks.
- Allows users to add tasks with customizable duration, categories, load types, priority, and circadian peak matching.
- Evaluates available windows based on circadian alignment and cognitive capacity forecasts (best choice, acceptable, not recommended).
- Provides task details displaying predicted energy impact, post-task battery levels, circadian match percentage, and cohort activity.

**Quick Actions & Energy Check-in**
- Provides quick options to add cognitive load-matched flexible activities, add fixed events/rigid blocks, or update current mental and physical states.
- Features an interactive energy check-in with sliders for Mental, Physical, and Social states to calibrate future scheduling predictions and slot recommendations.

**Insights & Trends**
- Provides workload insights including cumulative pressure and smart synthesis warnings regarding cognitive cliffs during prolonged study sessions.
- Analyzes real-time depletion across cognitive and energy vectors alongside bio-rhythm peak pacing patterns.
- Identifies draining activities versus restorative habits and features an "Auto-Pace Schedule" tool to apply restorative adjustments.

**Profile & Settings**
- Manages energy rhythm accounts, study programs (e.g., Computer Science & Math), weekly sync statuses, and focus balance.
- Configures capacity preferences including max focus limits, study rhythms, and auto-protect rest options.
- Controls preferences and tools such as smart notifications, recurring events, custom activity tags, feedback frequency, and dark mode.

Combine [Ideation Board](https://github.com/Jin-0804/daily-flow/blob/5c06dfb38a2d92905cc30c7392a085c7689c07d7/idea.drawio%20(1).png)

### 2.3 Mentor Consultation

| Date | Mentor | Feedback Received | What Was Changed |
|---|---|---|---|
| 8/9/2026 | Zach Khong | Focus more on personalisation by collecting text-based reflections after activities, information from AI agent conversations, and context shared during task planning. This information can help the system understand the student's preferences, experiences, and reasons. | Expanded the system to use personalised context alongside the energy-level system. Energy levels provide a deterministic basis for identifying suitable time slots, while the AI agent uses learned personal context to recommend the best-fit slot. Past experiences can also be reused to break large tasks into smaller steps and improve future recommendations as the student continues using the system. |

---

## 3.0 Design & Prototype

### Dashboard

**What it is:** A quick look at today — what's on, how your energy is, and what to focus on next.

**What you can do:**
- **See your energy** — Mental / Physical / Social levels and how much good focus time you have left.
- **See your tasks** — All of today's tasks with time and location.
- **Add something new** — Tap + Add Task to add a task for today.

### Agent – Schedule Helper

This is where you chat with your AI study helper.

**What it is:** A simple chat, like messaging someone who knows your schedule and tasks.

**What you can do:**
- **Ask anything** — "Explain entropy simply," "What's my day like?", "Help me plan my focus."
- **Get a plan** — The agent can break your study into small steps for you.
- **Use quick buttons** — Tap the little chips at the bottom for fast questions.

*Simple idea: if you're stuck or want help discussing your plan, just ask the agent here.*

### Add New Task — Popup

This is the quick way to add something new.

**What it is:** A small sheet that slides up when you tap + or Add Task.

**What you can do:**
- **Name your task** — like "Quantum Review" or "Gym".
- **Pick a type** — Focus, Lecture, Rest, or Sport.
- **Set how long** — choose 30 / 60 / 90 / 120 minutes, or type any number.
- **Add where** — like "Library" or "Hall 104".
- **Tap Add to Schedule** — it takes you to the weekly calendar where you pick the exact day and time. Green means good energy, red means slower — you can still drop it anywhere and hit Confirm.

When you add a task, you're brought to your calendar, where green shows suitable energy and red shows lower energy.

The task is automatically placed in a suitable green slot, and you can confirm it or drag it to another time.

If you're unsure, tap the agent icon to ask for the best time, and it will recommend a suitable slot based on your schedule.

### Calendar

See your time however you like.

**What it is:** Your schedule in three views — Daily, Weekly, Monthly.

**What you can do:**
- **Daily** — See today's timeline in order, with details for each task.
- **Weekly** — See the whole week. Days on the left, hours across the top. Green = good energy, red = slower. Swipe to see more hours.
- **Monthly** — See the whole month. Dots show days with tasks. Tap a day to jump to it.

*Simple idea: pick Day for detail, Week to plan the week, Month to get the big picture.*

### Profile

**What it is:** Your personal space — who you are and how your body and studies are doing.

**What you can do:**
- **See your profile** — Your name, study program, and status.
- **Change settings** — Update your study program or how your body is tracked.

*Simple idea: check here to see your info and keep your settings up to date.*

---

## 4. What Makes It Different

Our system goes beyond traditional task scheduling by combining energy-aware scheduling with personal context and continuous learning. Instead of only asking when a student is available, the system learns what works for the individual student and uses this information to improve future recommendations.

- **Personalised Time-Slot Recommendation** — Energy levels identify suitable time slots, while the AI uses the student's personal preferences, experiences, and context to recommend the best-fit slot.
- **Learning from Text Reflections** — Students can explain why an activity went well or poorly, giving the system context that numerical energy ratings alone cannot capture.
- **Personalised AI Agent** — The agent learns from conversations and planning discussions to understand the student's habits, preferences, and personal context.
- **Continuous Personalisation** — Past experiences are reused to improve future recommendations. The more the student uses the system, the better it understands what works for them.
- **Context-Aware Task Splitting** — The system uses past experiences to identify when a task may be difficult to complete in one session and suggest smaller, more manageable steps.
- **Energy + Personal Context** — The system combines a deterministic energy layer to identify suitable slots with an AI personalisation layer to recommend the best slot for the individual student.

### Existing Solution Comparisons

| Feature | Motion | Reclaim | Sunsama | Our System |
|---|---|---|---|---|
| Task & Calendar Scheduling | ✓ | ✓ | ✓ | ✓ |
| Priorities & Deadlines | ✓ | ✓ | ✓ | ✓ |
| Automatic Rescheduling | ✓ | ✓ | ✓ | ✓ |
| Workload Management | ✓ | ✓ | ✓ | ✓ |
| Mental / Physical / Social Energy Learning | — | — | — | ✓ |
| Personal Context from Reflections & Conversations | — | Limited | — | ✓ |
| Personalised Best-Slot Recommendation | ✓ | ✓ | ✓ | ✓ + personal context |
| Learns from Past Experiences | Limited | ✓ | Limited | ✓ |

---

## 5. Technical Architecture & Feasibility

### 5.1 Tech Stack

| Component | Technology | Why we chose it / Purpose | Expected Constraints |
|---|---|---|---|
| **Mobile Frontend** | React Native | Allows us to build the mobile application using a familiar JavaScript/TypeScript and web-based development approach. It also gives us the option to expand the application to a web interface in the future without completely rebuilding the frontend. | Some platform-specific behaviour may still require additional implementation for iOS and Android. |
| **Backend** | Bun | Provides a fast and lightweight runtime for our backend. It allows us to handle API requests, application logic, energy calculations, scheduling logic, and communication with other services using JavaScript/TypeScript. | — |
| **Database** | PostgreSQL + Prisma | PostgreSQL provides a reliable relational database that can be self-hosted easily. Prisma provides a convenient, type-safe SDK for interacting with the database and makes database development easier. | — |
| **Authentication** | OAuth | Provides a simple and secure way for users to sign in through supported authentication providers without requiring us to store user passwords ourselves. | — |
| **AI Agent** | OpenAI API + LangGraph | OpenAI provides the language model capabilities, while LangGraph allows us to structure the agent into multi-step workflows for retrieving user context, reasoning about scheduling options, and generating personalised recommendations. | API costs, latency, rate limits, and dependence on an external AI service. AI responses can also be inconsistent, so important scheduling constraints should be handled deterministically by the system. |
| **Scheduling & Workflows** | Temporal | Temporal provides reliable execution of scheduled and long-running workflows, such as recurring events, delayed tasks, reminders, and background scheduling processes. This allows workflows to continue reliably even if the backend temporarily restarts. | Temporal adds infrastructure complexity and requires additional resources to run and maintain. |
| **Application Hosting** | DigitalOcean | DigitalOcean provides a straightforward cloud environment for hosting our backend and supporting services. It gives us control over the infrastructure and is suitable for deploying self-hosted services such as PostgreSQL and Temporal. | — |
| **Containerisation** | Docker | We plan to use Docker when deploying the application so the backend and supporting services can be packaged with their required dependencies. This makes deployment and environment setup more consistent. | — |

### 5.2 System Architecture Diagram

*(See diagram in original document.)*

### 5.3 Build Plan & Scope

#### 5.3.1 Core System Overview

The system will be built around two complementary layers:

**Deterministic Energy Layer** — Determines which time slots are suitable based on the student's predicted mental, physical, and social energy levels.

**Personalisation Layer** — Uses the student's past experiences, reflections, preferences, and personal context to determine which suitable slot is the best fit and explain the recommendation.

#### 5.3.2 Student Schedule

The student first enters their commitments into the calendar. Events are divided into two types.

**Fixed Events** — Events that regularly occur at predictable times.
- Classes
- Badminton training
- Sleep
- Medication
- Recurring commitments

These events automatically appear on future dates according to their recurrence rules.

**Temporary Events** — Tasks or activities that need to be scheduled.
- Study Chemistry Chapter 9
- Complete an assignment section
- Mathematics tutorial
- Gym session

#### 5.3.3 Deterministic Energy Layer

This is the core energy-level system that will be implemented during the building phase.

The system represents the student's current capacity using three dimensions:
- 🧠 Mental
- 💪 Physical
- 👥 Social

Each dimension is represented on a 1–10 scale.

**Activity Feedback**

Before and after each activity, students will be notified to record their mental, physical, and social energy levels (1–10).

For example: Math Lecture

| | Mental | Physical | Social |
|---|---|---|---|
| Before | 8 | 6 | 7 |
| After | 6 | 8 | 6 |
| Observed change | −2 | 2 | −1 |

The system therefore learns that this type of activity has approximately: **Mental −2 | Physical 2 | Social −1**

Over multiple observations, the system maintains an updated estimate of the typical impact of that activity.

It learns, for each dimension:
- Activities that drain energy
- Activities or periods that restore energy

**Recovery is also learned**

Free time is treated as a recovery activity. The system compares energy before and after free periods to learn how much they restore the student.

**Activity Categories**

A major problem with learning activity impact is that every individual task should not be treated as completely different.

For example:
- Revision Math Chapter 1
- Revision Math Chapter 2
- Revision Chemistry Chapter 9

...are different tasks but may share a similar Revision activity profile.

Therefore, activities will use categories/tags such as: `[Revision]`

The system can then learn the typical impact of the activity category, rather than requiring completely separate data for every task name.

**Reducing Feedback Burden**

The system will initially request feedback more frequently for a new activity type. Once enough observations have been collected and the estimated impact becomes sufficiently stable, feedback requests will become less frequent.

The system can occasionally ask for confirmation to ensure that its estimate remains accurate.

This prevents the student from having to repeatedly provide feedback for activities whose impact is already well understood.

#### 5.3.5 Predicting Suitable Time Slots

When the student adds a task, the system evaluates the available time slots.

For example: Study Math Notes — 30 minutes

System will check available slots based on energy-level at specific timestamp:

| Time | Predicted Mental | Physical | Social |
|---|---|---|---|
| 10–11 AM | 4 | 6 | 3 |
| 2–3 PM | 7 | 5 | 7 |
| 6–7 PM | 5 | 8 | 8 |
| 8–9 PM | 6 | 8 | 8 |

The system calculates the student's predicted energy state at each candidate start time, based on the events leading up to that timestamp.

**Suitability Rules**

The system applies deterministic rules based on the task's requirements.

For a task requiring mental capacity:
- Mental capacity: ≥ 7/10
- Other dimensions: ≥ 5/10

- 2–3 PM: M7 / P5 / S7 → **Suitable ✓**
- 10–11 AM: M4 / P6 / S3 → **Not suitable ✕**

The deterministic layer makes this decision using predefined rules. This makes scheduling predictable, explainable, and testable.

**Recalculating Within a Time Slot**

The system also accounts for events occurring immediately before a task.

For example:
- 10:00–10:30 AM — Free
- 10:30–11:00 AM — Proposed Math Revision

The system cannot simply use the state calculated at 10:00 AM. It first applies the predicted recovery from the 10:00–10:30 AM free period, then calculates the student's state at 10:30 AM. It then evaluates whether the student meets the required capacity.

If the slot is unsuitable but the student chooses it anyway, the system provides a warning rather than preventing the student from making the choice.

#### 5.3.7 Personalised AI Agent

The AI agent sits on top of the deterministic energy layer. It receives structured suitability results and combines them with the student's personal context.

The agent learns from:
- Post-event reflections
- Agent conversations
- Planning discussions
- Preferences and past experiences
- Previous scheduling outcomes

For example, if the system identifies 2 PM, 6 PM, and 8 PM as suitable, the agent uses personal context to select the best fit.

> *"You usually focus better on Chemistry when studying with your friend, who is available around 2 PM."*
> **2 PM — Best fit**

The agent also acts as the interface to the system, allowing students to interact with their schedule and tasks through conversation. With access to the application's APIs, it can retrieve information and perform actions such as creating, editing, and rescheduling events.

- **Deterministic layer:** Which times are suitable?
- **Personalisation layer:** Which suitable time is best for this student?

This is the central architecture of the system.

#### 5.3.8 Structured Personal Memory

Important information from conversations and reflections is stored as structured personal context in the database, rather than only in conversation history.

For example:
- **Preference:** Prefers studying Chemistry with a friend.
- **Pattern:** Concentration decreases when studying Chemistry late at night.

This information can be reliably retrieved for future planning and personalisation.

- Conversation history → conversational context
- Personal context → important information retained for future use

This makes personalisation more reliable and prevents important information from being lost in conversation history.

#### 5.3.9 Task Breakdown

The agent can use past experiences to suggest breaking difficult tasks into manageable sessions. For example, if a 3-hour Biology assignment has previously caused the student to lose focus, it may recommend 3 × 1-hour sessions and schedule them within the suitable time regions identified by the deterministic layer.

## 🚀 Running the Prototype

No build step required — it's a static front-end prototype.

---

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
