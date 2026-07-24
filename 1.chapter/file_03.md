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