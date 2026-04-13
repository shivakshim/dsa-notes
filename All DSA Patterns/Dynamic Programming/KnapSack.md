
## What actually defines “Knapsack-type” DP

A problem is knapsack-type if:

1. You have **items / choices**
    
2. Each choice has a **cost** (consumes some resource)
    
3. You have a **capacity / limit**
    
4. You decide **how many times** to use each choice
    
5. You optimize / count / check feasibility under that constraint
    

That’s it.

No requirement of:

- explicit value field
    
- profit maximization
    
- weight–value pair
    

Those are **specific variants**, not the definition.

---

## Classical 0/1 Knapsack (baseline)

|Concept|Meaning|
|---|---|
|Item|object|
|Weight|cost|
|Value|profit|
|Capacity|limit|
|Goal|maximize profit|

---

## Coin Change (reframed properly)

Let’s rewrite coin change in knapsack language.

### Coin Change – “number of ways”

|Knapsack term|Coin Change equivalent|
|---|---|
|Item|coin denomination|
|Weight|coin value|
|Capacity|target sum|
|Value|**1 per valid combination**|
|Usage|unlimited (unbounded)|
|Goal|count ways|

There is **no profit to maximize**, but:

- you still **consume capacity**
    
- you still **choose items**
    
- you still obey **resource limits**
    

So it is an **unbounded knapsack variant**, but with a **different objective**.

---

## Why the missing “value” is not a problem

You’re thinking:

> “But knapsack has wt → val, coin change doesn’t”

That’s because you’re locking onto **one specific knapsack formulation**.

Knapsack DP is more general:

> **Knapsack = DP over choices with resource consumption**

What you _do_ with the result varies:

|Variant|What DP stores|
|---|---|
|0/1 knapsack|max value|
|Coin change (ways)|count|
|Coin change (min coins)|min|
|Subset sum|boolean|
|Partition|boolean / count|

Same structure. Different aggregation.

---

## Example: Coin Change = Unbounded Knapsack (min coins)

State:

`dp[s] = minimum coins to make sum s`

Transition:

`dp[s] = min(dp[s], 1 + dp[s - coin])`

That is **exactly unbounded knapsack**, except:

- “value” = 1 per coin
    
- optimization = min instead of max
    

---

## Why people loosely say “coin change is knapsack”

Because:

- Same DP table shape
    
- Same transitions
    
- Same capacity logic
    
- Same optimization patterns
    
- Same pitfalls (ordering, reuse, overcounting)
    

They are grouping by **DP structure**, not problem statement.

---

## Important distinction (this will save you later)

> **Knapsack is a DP pattern, not a story problem.**

House Robber  
Coin Change  
Subset Sum  
Partition  
Rod Cutting

All are **knapsack-family DP** even if:

- no “value”
    
- no “weight”
    
- no “bag”
    

---

## Final clarity (no contradictions)

- ❌ Coin change is NOT classical knapsack
    
- ✅ Coin change IS knapsack-family DP
    
- ❌ Weight→value mapping is NOT mandatory
    
- ✅ Resource-constraint DP is the core idea
    

---

### One sentence to lock it in

> **If a DP problem is about making choices under a capacity constraint, it lives in the knapsack family — regardless of whether it talks about profit, coins, or sums.**

That’s the clean, correct mental model.