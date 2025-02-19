# Learnings !
# Technical Interview Preparation

## Object-Oriented Programming (OOP) Questions

1. **What are the four principles of OOP? Explain each with examples.**
2. **What is the difference between class-based and prototype-based inheritance?**
3. **Explain method overloading and method overriding with examples.**
4. **What is the significance of the `this` keyword in JavaScript OOP?**
5. **How does JavaScript handle encapsulation since it lacks access modifiers like `private` or `protected`?**
6. **What are mixins in JavaScript? Provide an example.**
7. **How does polymorphism work in JavaScript? Provide an example.**
8. **Explain how object composition is an alternative to inheritance in JavaScript.**
9. **What is the purpose of the `super` keyword in JavaScript? Provide an example.**
10. **What is an abstract class in JavaScript, and how can you implement one?**

## Data Structures & Algorithms Questions

1. **Explain the differences between arrays and linked lists.**
2. **How does a hash table work?**
3. **What are the time complexities of different sorting algorithms (Bubble, Merge, Quick)?**
4. **Implement a binary search algorithm in JavaScript.**
5. **What is the difference between BFS and DFS? Provide a scenario where one is preferred over the other.**
6. **Explain the concept of memoization and implement a Fibonacci sequence using it.**
7. **How do you detect a cycle in a linked list?**
8. **Implement a stack and queue using JavaScript.**
9. **What is a priority queue, and how does it differ from a normal queue?**
10. **Write a function to find the longest substring without repeating characters.**

## Web Architecture Questions

1. **What is the difference between monolithic and microservices architecture?**
2. **Explain how a browser renders a web page step by step.**
3. **What is the role of CDN in web performance?**
4. **What is CORS, and why is it important?**
5. **Explain the concept of lazy loading and its benefits.**
6. **What are REST and GraphQL? How do they differ?**
7. **What are JWT and OAuth? How do they work?**
8. **How does load balancing improve application performance?**
9. **What are web sockets, and how are they different from HTTP?**
10. **Explain server-side rendering (SSR) vs client-side rendering (CSR) in React.**

## JavaScript & React Coding Questions

1. **What is event delegation in JavaScript, and why is it useful?**
2. **How does the event loop work in JavaScript?**
3. **What is the difference between `map`, `forEach`, `filter`, and `reduce`?**
4. **How does JavaScript handle asynchronous operations? Explain with examples.**
5. **Explain closures in JavaScript with a practical example.**
6. **What is the difference between `var`, `let`, and `const`?**
7. **What are higher-order functions in JavaScript? Provide an example.**
8. **Explain `debounce` and `throttle` functions with examples.**
9. **What are the key differences between shallow and deep copies in JavaScript?**
10. **How do you implement memoization in JavaScript?**

### React Coding Questions

1. **What is the difference between functional and class components in React?**
2. **How do you manage state in React without Redux?**
3. **Explain the use of `useEffect` hook with examples.**
4. **What is the purpose of `useMemo` and `useCallback` hooks?**
5. **How do you optimize performance in a large React application?**
6. **What is React context API, and how does it work?**
7. **How does React handle reconciliation and virtual DOM updates?**
8. **How do you implement a custom hook in React?**
9. **Explain React's error boundaries and how they work.**
10. **What are React fragments, and when should they be used?**

## JavaScript & React Machine Coding Questions

### 1. To-Do List (Redux Version)

```jsx
import { useState } from "react";
import { useDispatch, useSelector } from "react-redux";

const ADD_TASK = "ADD_TASK";
const TOGGLE_TASK = "TOGGLE_TASK";

const addTask = (text) => ({ type: ADD_TASK, payload: text });
const toggleTask = (index) => ({ type: TOGGLE_TASK, payload: index });

const todoReducer = (state = [], action) => {
  switch (action.type) {
    case ADD_TASK:
      return [...state, { text: action.payload, completed: false }];
    case TOGGLE_TASK:
      return state.map((task, i) => i === action.payload ? { ...task, completed: !task.completed } : task);
    default:
      return state;
  }
};

function TodoApp() {
  const [task, setTask] = useState("");
  const dispatch = useDispatch();
  const tasks = useSelector(state => state);

  return (
    <div>
      <input value={task} onChange={(e) => setTask(e.target.value)} />
      <button onClick={() => { dispatch(addTask(task)); setTask(""); }}>Add Task</button>
      <ul>
        {tasks.map((t, index) => (
          <li key={index} style={{ textDecoration: t.completed ? "line-through" : "none" }}>
            {t.text} <button onClick={() => dispatch(toggleTask(index))}>Toggle</button>
          </li>
        ))}
      </ul>
    </div>
  );
}
export default TodoApp;
```

### 2. Star Rating Component

```jsx
import { useState } from "react";

function StarRating({ totalStars = 5 }) {
  const [rating, setRating] = useState(0);
  return (
    <div>
      {[...Array(totalStars)].map((_, i) => (
        <span key={i} onClick={() => setRating(i + 1)} style={{ cursor: "pointer", color: i < rating ? "gold" : "gray" }}>
          ★
        </span>
      ))}
    </div>
  );
}
export default StarRating;
```

### 3. Render Object Data in Table

```jsx
function DataTable({ data }) {
  return (
    <table border="1">
      <thead>
        <tr>
          {Object.keys(data[0]).map((key) => (
            <th key={key}>{key}</th>
          ))}
        </tr>
      </thead>
      <tbody>
        {data.map((row, i) => (
          <tr key={i}>
            {Object.values(row).map((val, j) => (
              <td key={j}>{val}</td>
            ))}
          </tr>
        ))}
      </tbody>
    </table>
  );
}
export default DataTable;
```

This document provides a structured preparation for your interview, covering OOP, data structures, web architecture, JavaScript, React, and coding challenges. Good luck!

