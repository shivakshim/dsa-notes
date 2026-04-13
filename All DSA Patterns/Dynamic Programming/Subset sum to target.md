> In Subset Sum, the same state `(i, sum)` is NOT guaranteed to repeat.  
> It may or may not happen.  
> If it doesn’t happen (like in `[2,3,4,5]`), DP gives no benefit.  
> So with a big input of that type, won’t it still TLE?  
> Then how is DP _guaranteed_ to work?”

This is a **100% valid logical concern**.