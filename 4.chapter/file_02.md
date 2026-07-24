Q2. Can you give an example where useMemo/useCallback made performance worse or was unnecessary?

A2. ❌ DON'T MEMOIZE IF:
- Operation takes < 1ms
- Props/dependencies change on every render
- You haven't measured performance
- Code becomes less readable
- No child component benefits

✅ ONLY MEMOIZE IF:
- Measured with React DevTools Profiler
- Operation takes > 10ms
- Re-render is actually preventable
- Component is re-rendering > 3x unnecessarily
- Code stays maintainable