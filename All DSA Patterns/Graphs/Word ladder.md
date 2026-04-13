## The 5-SECOND GRAPH DETECTOR 🧠⚡

When you read a problem, ask **these 3 questions in order**:

---

### 🔍 Q1. “What is a STATE here?”

If the problem talks about:

- a **configuration**
    
- a **string**
    
- a **number**
    
- a **board**
    
- a **position**
    
- a **combination**
    

👉 That thing is a **node**.

**Word Ladder**

- State = _current word_  
    → **Node = word**
    

---

### 🔍 Q2. “Can I move from one state to another by a RULE?”

Look for phrases like:

- “change one letter”
    
- “one operation”
    
- “one move”
    
- “one mutation”
    
- “one swap”
    

👉 That rule defines an **edge**.

**Word Ladder**

- Rule = _change exactly one character_  
    → **Edge exists**
    

---

### 🔍 Q3. “Do they ask for minimum steps / shortest sequence?”

If YES → **BFS on a graph**.

**Word Ladder**

- “shortest transformation sequence”  
    → BFS screaming at you.
    

---

## Put together (this is the unlock 🔓)

> **STATE + RULE + SHORTEST = GRAPH BFS**

Word Ladder hits **all three**.

---

## Why your brain didn’t recognize it immediately (normal af)

Because:

- No “nodes” word
    
- No “edges” word
    
- No adjacency list
    
- No graph drawing
    

But **graphs are about relationships**, not drawings.

---

## Let me prove this with brutal examples

### Example 1: Lock problem (0000 → 1234)

- State = lock number
    
- Rule = rotate digit
    
- Shortest moves
    

👉 Graph BFS

---

### Example 2: Minimum mutations (gene string)

- State = gene string
    
- Rule = change one char
    
- Shortest path
    

👉 Graph BFS

---

### Example 3: Word Ladder

- State = word
    
- Rule = change one char
    
- Shortest path
    

👉 SAME DAMN THING.

Different skin. Same skeleton.

---

## The “hidden graph” pattern 🕵️‍♀️

Word Ladder is in the family of:

- **State-space graphs**
    
- **Implicit graphs**
    

You don’t see nodes/edges — you **generate** them.

---

## Interview-level recognition rule 🎤

Say this out loud once:

> “If I can model each configuration as a node and transitions as edges, it’s a graph problem.”

That sentence is your compass.

---

## Why grid problems felt easier to recognize

Because:

- Grid = visual graph
    
- Neighbors = obvious
    

Word Ladder = abstract graph  
Same math. Less visual.

---

## Final mental tattoo 🧠

`IF:   • there is a state   • there is a valid move   • there is a shortest / minimum ask THEN:   → GRAPH + BFS`

No exceptions. Zero.

---

## TL;DR (the answer to your question)

> You don’t recognize Word Ladder as a graph by looking at the data structure.  
> You recognize it by identifying **state transitions** and **shortest path**.