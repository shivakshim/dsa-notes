### 🧠 First principle:

Ask yourself this one simple question before sorting:

> “What am I **trying to control** — the _start time_ of things or the _end time_ of things?”

That’s literally the switch.  
There are two kinds of interval problems in the world:

---

## 🩵 1. **When you need to MERGE or TRAVERSE sequentially**

→ Sort by **start** time.

Because merging means:

> “Let me see what starts next, and check if it _begins before_ the previous one ends.”

You don’t care about who ends first —  
you just move left-to-right by the next starting interval.

### Examples:

- **Merge Intervals (LC 56)** ✅
- **Insert Interval (LC 57)**
- **Summary Ranges**

👉 Sort by `start`,  
then check:  
`if (next.start <= prev.end)` → overlap

---

## ❤️ 2. **When you need to PICK MAX/MIN intervals (non-overlapping sets)**

→ Sort by **end** time.

Because now your goal is:

> “Pick the interval that finishes earliest, so I can fit more stuff after it.”

That’s the “Activity Selection Problem” or “Meeting Scheduling” type.

### Examples:

- **Non-overlapping Intervals (LC 435)**
- **Maximum Meetings in a Room (GFG)**
- **Minimum Number of Arrows to Burst Balloons (LC 452)**
- **Course Schedule III (LC 630)**

👉 Sort by `end`,  
then greedily pick an interval if its `start >= lastEnd`.

---

## 🧩 TL;DR Rule of Thumb:

|Goal|Sort by|Why|
|---|---|---|
|Merging or combining overlapping ranges|**Start**|You care about sequence order|
|Selecting maximum non-overlapping intervals|**End**|You care about earliest finishing|
|Minimizing resources (platforms, arrows, rooms)|**Start** & **End** separately|You simulate entry/exit|

---

### 🧠 How to think _intuitively_:

- If you’re **traversing** → “Who comes next?” → sort by **start**.
- If you’re **choosing** → “Who leaves earliest?” → sort by **end**.
- If you’re **counting simultaneous stuff** (like platforms) → you don’t sort pairs, you sort **both arrays separately**.

---

### ⚡ Quick analogy:

Think of it like relationships 😂

- **Start sort:** you’re going through one by one, seeing if the new one _overlaps_ your past baggage.
- **End sort:** you’re being strategic — ending old ones fast so you can fit more new ones later 😭💀