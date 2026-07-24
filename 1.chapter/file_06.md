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