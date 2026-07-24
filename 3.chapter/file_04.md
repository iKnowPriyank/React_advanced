Q4. useRef — beyond DOM references, what else is it used for?
A.4 useRef has 3 main uses beyond DOM:

1. Store mutable values that persist across re-renders

Ex. const intervalRef = useRef(null);
intervalRef.current = setInterval(...);
// Survives re-renders! Can be cleared later

2. Debounce/track IDs without re-renders

Ex. const timeoutRef = useRef(null);
// Clear timeout and set new one
// NO re-render needed

3. Keep component state WITHOUT triggering re-renders

Ex. const stateRef = useRef({ count: 0 });
stateRef.current.count++;
// State tracked, no re-render, better performance

---

Key difference from useState:

useState triggers re-render
useRef doesn't trigger re-render
When to use ref:

Storing timer/request IDs
Tracking previous values
Debouncing without re-renders
Performance tracking
Don't use ref for:

Anything that needs to update the UI
Component state that affects render"