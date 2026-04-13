
- Since both patterns involves 2 pointers moving in different paces actually both are variations of fast & slow pointers.
- But only the 1st is considered as actual fast 7 slow pointer pattern that has key factor as collision or meeting.

#### **🔁1. Linked List Style (Actual Fast & Slow Pointers)**
 🙅‍♂️**Key trait**: The speed difference is _essential_ to meet/collide.
  🆔Key-Word - speed difference
  
- **One moves 1 step, the other 2 steps** (or different speeds).
- It is all about Collision/meeting of 2 pointers.
- Classic examples:
    - Linked list cycle detection (Floyd's).
    - Find start of cycle.
    - Find middle of linked list.
    - Happy number problem.


#### **🔀2. Staggered Two-Pointer Scanning 
🙅‍♂️**Key trait**: Both move one step at a time (fast does the scanning, slow decides what to keep). Not about **relative speed**.
🆔Key-Word - scan & check

- Called "fast/slow" sometimes, but really it's just **scan + write/scan + check**.
- This isn't about meeting, its just moving both forward based on some check/condition.
- Examples:
    - Remove duplicates from sorted array (LC 26).
    - Move zeroes.
    - Remove elements

So yeah — they both get tossed into the "two-pointer/fast-slow" bucket, but they're **not the same pattern**.  
One is **speed-based collision**, the other is **in-place array editing**.
