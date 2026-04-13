#### ✅ 1. XOR Basics (The Holy Trinity)

- `a ^ a = 0` (number XOR itself → zero)
- `a ^ 0 = a` (number XOR zero → same number)
- XOR is **commutative and associative** → order doesn’t matter.

#### ✅ 2. Prefix XOR Concept

Exactly like prefix sum, but XOR instead of `+`.
`prefixXor[i] = arr[0] ^ arr[1] ^ ... ^ arr[i]`

🙅‍♂️For any subarray `(l, r)`:
`XOR(l..r) = prefixXor[r] ^ prefixXor[l-1]`
not subtraction but prefix because it inverses itself ,so this will remove common part -> 0 - (l-1)
(because overlapping part cancels out).

####  ✅ 3. Core Intuition:

When XOR from 0 to r is `P`, and XOR from 0 to l-1 is also `P`, then subarray (l..r) XOR = `0`.  
This is similar to prefix sum where `sum[r] - sum[l-1] = 0`.

#### ✅ 4. Recognition Cues:

- Query: "XOR of subarray" or "count subarrays with XOR condition".
- Keywords: XOR, subarray, prefix, equal XOR, queries.