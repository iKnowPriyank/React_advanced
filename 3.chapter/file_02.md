Q2. useEffect — dependency array rules and common mistakes.

useEffect(() => {
Effect code runs here
}, [dependency1, dependency2]);
↑ Dependency array controls when effect runs

Dependency array does 3 things:

[] → Runs once (on mount)
[dep] → Runs when dep changes
No array → Runs after EVERY render (bad!)


"useEffect dependency rules:-
Include all external values used (or you get stale data)
Empty array [] = run once on mount
With deps = run when deps change
No array = run every render (usually wrong)

Common mistakes:-
Missing dependencies (stale closures)
Infinite loops (setting state in effect without deps)
No cleanup (memory leaks)
New objects in deps (effect runs constantly)
