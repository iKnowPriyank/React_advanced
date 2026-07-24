
Q2. Controlled vs uncontrolled components — trade-offs and when to choose each.

A2. Controlled Components:- A controlled component has its value managed by React state. Every change goes through React:

const [value, setValue] = useState('');
<input value={value} onChange={(e) => setValue(e.target.value)} />

React is the single source of truth for the input value.

Advantages:
1. Real-time validation is straightforward
2. Easy to implement conditional logic based on input
3. Can programmatically set or clear values
4. Easy to integrate with other form fields
5. Supports dependent fields naturally

Disadvantages:
1. More boilerplate code
2. Re-renders on every keystroke (can affect performance with complex logic)
3. Updates go through React pipeline (state update → re-render → DOM update)

Uncontrolled Components:
An uncontrolled component stores its value in the DOM, accessed via refs:

const inputRef = useRef(null);
<input ref={inputRef} defaultValue=\"initial\" />
// Access with: inputRef.current.value

The DOM is the single source of truth.

Advantages:
1. Less code needed
2. No re-renders on input changes
3. Better for integrating with non-React code
4. Only way to handle file inputs
5. Better performance for simple forms

Disadvantages:
1. Harder to validate in real-time
2. Can't easily disable buttons based on input
3. More manual work with multiple fields
4. Harder to manipulate values programmatically

When to Choose:

Controlled:- Most of the time. Default choice. Use when you need real-time feedback, validation, or logic based on input values.
Uncontrolled:- For file inputs, simple forms with only submit needed, integration with third-party libraries, or when you specifically need to avoid re-renders.