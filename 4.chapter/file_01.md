Q1. useMemo vs useCallback vs React.memo — precise distinctions and when each actually helps.

A1. React.memo = Prevent re-render if props didn't change
useMemo = Prevent expensive calculation if deps didn't change
useCallback = Prevent function recreation if deps didn't change

They solve the same problem in different ways:

1. Problem: Unnecessary re-renders/calculations
2. React.memo: Blocks re-render at component level
3. useMemo: Blocks calculation at value level
4. useCallback: Blocks function recreation at function level

Visual Comparison 📊

PROBLEM:
Parent re-renders → Child re-renders → Expensive calculation → Slow UI

SOLUTIONS:

React.memo:
Parent re-renders → Child checks props → Props same? → NO re-render ✅

useMemo:
Calculation runs → Result cached → Deps same? → Return cached result ✅

useCallback:
Function created → Reference cached → Deps same? → Return same reference ✅