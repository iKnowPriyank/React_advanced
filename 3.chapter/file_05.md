Q5. useImperativeHandle — what problem does it solve, and why should it be used sparingly?

A5. useImperativeHandle = Expose imperative methods from a child component to a parent

// Parent says: "Child, I want to call methods on you directly"
// Child says: "OK, here are the methods you can call"

The Problem It Solves 🎯
Scenario: Parent Needs to Control Child Directly
The Problem (Without useImperativeHandle):

// Child component
function TextInput({ initialValue }) {
  const [value, setValue] = useState(initialValue);
  
  return (
    <input 
      value={value}
      onChange={(e) => setValue(e.target.value)}
    />
  );
}

// Parent component
function Form() {
  const inputRef = useRef(null);
  
  const handleReset = () => {
    // ❌ Problem: Can't reach the input's state!
    // How do I clear the input?
    // I can access the DOM element: inputRef.current
    // But I can't call methods on the component
  };
  
  return (
    <div>
      <TextInput ref={inputRef} initialValue="" />
      <button onClick={handleReset}>Reset</button>
    </div>
  );
}

// ❌ Parent can't tell child: "Clear your input!"
// ❌ Parent can't trigger child's methods
// ❌ Bad separation of concerns

----------------------------------------------------------------------

The Solution: useImperativeHandle

// Child component
function TextInput({ initialValue }, ref) {
  const [value, setValue] = useState(initialValue);
  const inputRef = useRef(null);
  
  useImperativeHandle(ref, () => ({
    // Expose methods that parent can call
    clear: () => {
      setValue('');
      inputRef.current.focus();
    },
    
    getValue: () => value,
    
    setValue: (newValue) => setValue(newValue),
    
    focus: () => {
      inputRef.current.focus();
    }
  }), []);
  
  return (
    <input 
      ref={inputRef}
      value={value}
      onChange={(e) => setValue(e.target.value)}
    />
  );
}

// Wrap with forwardRef
export default forwardRef(TextInput);

// Parent component
function Form() {
  const inputRef = useRef(null);
  
  const handleReset = () => {
    // ✅ Now parent can call child's methods!
    inputRef.current.clear();
  };
  
  const handleSetValue = () => {
    inputRef.current.setValue('Hello');
  };
  
  const handleFocus = () => {
    inputRef.current.focus();
  };
  
  return (
    <div>
      <TextInput ref={inputRef} initialValue="" />
      <button onClick={handleReset}>Reset</button>
      <button onClick={handleSetValue}>Set "Hello"</button>
      <button onClick={handleFocus}>Focus</button>
    </div>
  );
}