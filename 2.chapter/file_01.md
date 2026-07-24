Q1. What is JSX actually compiled to, and why does that matter for performance/debugging?

A.1 JSX is not valid JavaScript, so it's compiled to React.createElement() calls before the code runs. For example, <div>Hello</div> becomes React.createElement('div', null, 'Hello').

This matters for performance because creating objects on every render can be expensive, and it matters for debugging because error messages and DevTools reference the compiled code, not the JSX you wrote."

Detailed Answer:
"JSX is syntactic sugar that makes React code easier to write. During compilation (by Babel), JSX is transformed into React.createElement() function calls."