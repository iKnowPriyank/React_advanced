Q1. What is the Virtual DOM and why does React use it?

A1. Virtual DOM is a lightweight copy of the Real DOM kept in memory. When state changes, React updates the Virtual DOM first, compares it with the previous version, finds the differences, and updates only those specific parts in the Real DOM. This makes React fast and efficient.