---
layout: default
title: React Design Patterns
nav_order: 3
toc: true
toc_sticky: true
---

# 🎯 Advanced React Design Patterns 

## Why Design Patterns in React?

Design patterns are reusable solutions to common problems in React architecture. For experienced devs, this session can:

- Sharpen component architecture skills
- Encourage building reusable, maintainable code
- Improve understanding of trade-offs in implementation

---

## 📘 React Design Patterns (with Use Cases)

### 1. 🔁 Container-Presenter (Smart-Dumb) Pattern

**Use When:** You want to separate logic from UI\
**Example:**

- `UserListContainer`: Fetches data
- `UserList`: Pure UI\
  **Benefit:** Testable, isolated presentation logic

---

### 2. 🧩 Compound Components

**Use When:** You have tightly related components that need to share implicit state\
**Example:**

```jsx
<Tabs>
  <Tabs.List />
  <Tabs.Panel />
</Tabs>
```

**Mechanism:** Shared context under the hood

---

### 3. 💡 Render Props Pattern

**Use When:** You want to share logic between components without HOCs\
**Example:**

```jsx
<MouseTracker render={({ x, y }) => <h1>{x},{y}</h1>} />
```

---

### 4. 🔁 Higher-Order Components (HOC)

**Use When:** You want to enhance a component by wrapping it\
**Example:**

```jsx
const withLoading = (Component) => (props) =>
  props.loading ? <Spinner /> : <Component {...props} />;
```

---

### 5. 🧵 Hooks-Based Composition

**Use When:** You want reusable logic in a functional world\
**Example:**

```jsx
function useDebounce(value, delay) {
  const [debounced, setDebounced] = useState(value);
  // debounce logic
  return debounced;
}
```

---

### 6. 🧱 Slot Pattern

**Use When:** You want to give control of layout to the parent\
**Example:**

```jsx
<Card>
  <Card.Header>Title</Card.Header>
  <Card.Body>Content</Card.Body>
</Card>
```

---

### 7. 🧩 State Reducer Pattern

**Use When:** You want to give users full control over state transitions\
**Used In:** `Downshift`, `React-Select`\
**Idea:** Let user pass a reducer to handle state

---

### 8. 🔄 Controlled vs Uncontrolled Components

- **Controlled:** State handled by parent
- **Uncontrolled:** Internally managed state, exposed via refs

---

### 9. 🧠 Inversion of Control via Context

**Mechanism:** Custom providers that inject dependencies (e.g., API, theme)\
**Use Case:** Multi-tenant or plugin-based architecture

---

## 🧪 Optional Bonus Patterns

- **Observer Pattern:** React’s own reactivity model
- **Singleton:** ThemeProvider or i18n service
- **Factory Pattern:** Component factories for dynamic rendering


---

## 🧪 Mini Workshop Exercise for Devs

### Goal: Refactor a messy component using a better pattern

### Scenario:

You are given a monolithic `Modal` component that has state, logic, and rendering tightly coupled.

```jsx
function Modal({ isOpen, onClose }) {
  const [inputValue, setInputValue] = useState('');

  if (!isOpen) return null;

  return (
    <div className="modal">
      <div className="header">Modal Title</div>
      <input
        value={inputValue}
        onChange={(e) => setInputValue(e.target.value)}
      />
      <button onClick={onClose}>Close</button>
    </div>
  );
}
```

### Task:

Refactor the modal using:

- Compound Component pattern (`Modal.Header`, `Modal.Body`, `Modal.Footer`)
- Externalize internal state using `useModal()` custom hook

### Bonus:

- Add accessibility (ESC to close, focus trap)
- Add TypeScript types

---

Happy coding 🚀

