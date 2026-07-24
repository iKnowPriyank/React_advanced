Q3. useLayoutEffect vs useEffect — concrete case where the choice matters.

The Key Difference ⚡
useEffect: Runs AFTER browser paints
useLayoutEffect: Runs BEFORE browser paints

Q: Why not always use useLayoutEffect?

"Because it blocks the browser from painting. If useLayoutEffect takes 200ms, the user doesn't see anything for 200ms. useEffect doesn't block, so the screen paints immediately (even if effect is slow). Use useLayoutEffect only when you NEED something before paint."

When to Use useLayoutEffect - Complete Guide
The Simple Rule 🎯
Use useLayoutEffect ONLY when:

You need to measure DOM (getBoundingClientRect, offsetWidth, etc.)
You need to change DOM based on measurements
Before the browser paints (to avoid flicker)