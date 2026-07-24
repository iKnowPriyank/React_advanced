Q1. useState — batching behavior, and functional vs direct updates.

A1. Batching:

React 18+ automatically batches multiple state updates into a single re-render
Event handlers, useEffect, setTimeout all batched
React 17 doesn't batch setTimeout/Promises

Q:2 What about async state updates?

A:2 "In React 18+, even async updates (setTimeout, fetch) are batched. In React 17, they're not. This was a major improvement in React 18."

Note :- "Huge. Without batching, 10 state updates = 10 re-renders. With batching, 10 state updates = 1 re-render. That's 10x better performance."