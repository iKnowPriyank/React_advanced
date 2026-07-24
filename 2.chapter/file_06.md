Q6. Class components vs function components — what's actually different today?
A6. "Class vs Function Components - What's Different:


State:-
Class: this.state = {count: 0} and this.setState()
Function: const [count, setCount] = useState(0) and setCount()
Functions are simpler!

Lifecycle:-
Class: componentDidMount(), componentDidUpdate(), componentWillUnmount()
Function: useEffect() hook handles all
Functions are cleaner!

Props:-
Class: this.props.name
Function: {name} (destructured)
Functions are cleaner!


This binding:-
Class: Must bind methods (confusing!)
Function: No this needed
Functions are simpler!

Code length:-
Class: More boilerplate
Function: Less code
Functions win!