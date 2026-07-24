Q.4 What is a Portal? 🚪
A.4 Portal = A way to render a component OUTSIDE of its parent's DOM tree

Normal rendering:
┌─────────────────────┐
│   <div id="root">   │
│  ┌───────────────┐  │
│  │   MyApp       │  │
│  │ ┌───────────┐ │  │
│  │ │ Modal     │ │  │ ← Modal is INSIDE App
│  │ └───────────┘ │  │
│  └───────────────┘  │
│                     │
└─────────────────────┘

Portal rendering:
┌─────────────────────┐          ┌──────────────┐
│   <div id="root">   │          │ <div id=     │
│  ┌───────────────┐  │          │  "portal">   │
│  │   MyApp       │  │          │┌────────────┐│
│  │ (Modal code)  │  │          ││ Modal      ││ ← Modal is OUTSIDE App!
│  └───────────────┘  │          │└────────────┘│
│                     │          │              │
└─────────────────────┘          └──────────────┘

With Portal: Modal is rendered somewhere else (outside App)

App
├── Header
└── Content

Modal ← Rendered HERE (outside!)