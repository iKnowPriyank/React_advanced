Q1. What is the Virtual DOM and why does React use it?

A1. Virtual DOM is a lightweight copy of the Real DOM kept in memory. When state changes, React updates the Virtual DOM first, compares it with the previous version, finds the differences, and updates only those specific parts in the Real DOM. This makes React fast and efficient.

---

Q2. Explain React's diffing/reconciliation algorithm and its heuristics?

A2. React's diffing algorithm compares the old and new Virtual DOM trees to find differences. It uses smart rules like: if element types are different, it replaces the whole tree; if they're the same, it updates only attributes. For lists, React uses keys to identify which items changed, moved, or were added/removed. This makes updates very efficient.

---

Q3. What is Fiber, and why was React rewritten around it (React 16)?
A3. React Fiber is a complete rewrite of React's core algorithm, introduced in React 16.

The main problem it solved: Old React would block the main thread while updating components, causing the UI to freeze during large updates.

Fiber's key features:-

1. Incremental rendering: Break work into small units that can be paused
2. Priority-based updates: High-priority updates (like user input) interrupt low-priority work
3. Ability to pause, abort, or resume work
4. Better support for async rendering and Suspense

Example: If you're typing in a search box while React is rendering 1000 search results, Fiber pauses the rendering, updates the input immediately, then continues rendering results. This creates a smoother user experience.

Fiber enables features like Concurrent Mode, Suspense, and time-slicing, making React suitable for complex, interactive applications.

---

Q4. What's the difference between Fiber and Virtual DOM?
A4. "Virtual DOM is what React updates (the copy of the DOM). Fiber is how React manages those updates (the scheduling system)."

---

Q5. What is Concurrent Mode?
A5. "It's a feature enabled by Fiber where React can work on multiple state updates at the same time and choose which to show based on priority."

---

Q6. What are 'render phase' and 'commit phase' in React, and why does the distinction matter?

A6. Breaking down the words:
Render Phase = Planning what to change (like making a to-do list 📝)
Commit Phase = Actually doing the changes (like crossing items off the list ✅)
Distinction = Understanding the difference between them

User clicks button
↓
┌──────────────────────────────────────┐
│ RENDER PHASE (Can be slow) │
│ ✓ Call component functions │
│ ✓ Create Virtual DOM │
│ ✓ Compare (diffing) │
│ ✓ Calculate changes │
│ ⏸️ Can pause here if needed │
│ 🔄 Can restart if needed │
└──────────────────────────────────────┘
↓
┌──────────────────────────────────────┐
│ COMMIT PHASE (Very fast!) │
│ ✓ Update Real DOM │
│ ✓ Run useLayoutEffect │
│ ✓ Paint screen │
│ ✓ Run useEffect │
│ ⚡ Can't interrupt! │
└──────────────────────────────────────┘
↓
User sees changes! 🎉

---

Q7. Why are keys important in lists, and what problems arise from using array index as a key?

A7. Keys are unique identifiers that help React recognize which items have changed, been added, or removed. They're like ID cards for list items.

"Using array index as a key is problematic because indices change when you add, remove, or reorder items. When indices change, React can't identify which item is which, leading to:

Unnecessary re-renders
State getting mixed up between items
Input values appearing on wrong items

---

Q6. What triggers a re-render in React?
A.8 
┌─────────────────────────────────────────┐
│  WHAT MAKES REACT RE-RENDER?            │
├─────────────────────────────────────────┤
│ 1. State changes (useState)             │
│ 2. Props changes (parent updates props) │
│ 3. Parent component re-renders          │
│ 4. Context changes                      │
│ 5. Key changes (in lists)               │
└─────────────────────────────────────────┘