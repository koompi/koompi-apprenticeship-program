# Level 2.6: React Fundamentals

## Track 02: Web Development

---

## 🎯 Level Overview

**React** is a JavaScript library for building user interfaces. It's used by Facebook, Instagram, Netflix, Airbnb, and many more.

**Duration**: 4-6 weeks

**Modules in this Level:**

1. Introduction to React
2. Components & Props
3. State & Events
4. Hooks (useState, useEffect)
5. React Router
6. Project: Task Manager App

---

## Prerequisites

- ✅ Completed JavaScript Basics & Advanced
- ✅ Understanding of ES6+ features
- ✅ Git & GitHub skills
- ✅ Node.js installed

---

## Why React?

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    WHY LEARN REACT?                                          │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   TRADITIONAL WEBSITE                   REACT APPLICATION                   │
│   ════════════════════                  ═══════════════════                 │
│                                                                              │
│   Full page reloads                    Only updates what changed           │
│   Hard to manage complexity            Components organize code             │
│   Repeat similar code                  Reusable components                  │
│   State scattered                      State management                     │
│                                                                              │
│   JOB MARKET                           USED BY                              │
│   ══════════                           ═══════                              │
│   #1 most wanted skill                 Facebook, Instagram                  │
│   High demand, good salary             Netflix, Airbnb                      │
│   Many jobs in Cambodia                Discord, Notion                      │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## What You'll Build

A **Task Manager Application**:

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                              │
│   📝 TASK MANAGER                                    [+ Add Task]           │
│                                                                              │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │  [ All ] [ Active ] [ Completed ]                                   │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │  ☐  Learn React basics                               [Edit] [🗑️]   │   │
│   │      Due: Dec 28, 2024      Priority: High                         │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │  ☑  Complete JavaScript project                      [Edit] [🗑️]   │   │
│   │      Due: Dec 25, 2024      Priority: High           ✓ Completed   │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │  ☐  Read documentation                               [Edit] [🗑️]   │   │
│   │      Due: Dec 30, 2024      Priority: Medium                       │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
│   Tasks: 2 active, 1 completed                                              │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Module Index

| Module | Topic | Key Concepts |
|--------|-------|--------------|
| 01 | Introduction | What React is, JSX, setup |
| 02 | Components | Functional components, props |
| 03 | State & Events | useState, handling events |
| 04 | Hooks | useEffect, custom hooks |
| 05 | Routing | React Router, navigation |
| 06 | Project | Task Manager App |

---

## React Code Preview

### A Simple Component

```jsx
function Welcome({ name }) {
    return (
        <div className="welcome">
            <h1>Hello, {name}!</h1>
            <p>Welcome to KOOMPI</p>
        </div>
    );
}

// Usage
<Welcome name="Sokha" />
```

### State Management

```jsx
import { useState } from 'react';

function Counter() {
    const [count, setCount] = useState(0);
    
    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={() => setCount(count + 1)}>
                Increment
            </button>
        </div>
    );
}
```

---

## Setup

### Create React App (with Vite)

```bash
npm create vite@latest my-app -- --template react
cd my-app
npm install
npm run dev
```

---

## Level Completion

**To complete Level 2.6:**

- [ ] All 6 modules studied
- [ ] Understand components and props
- [ ] Use React hooks (useState, useEffect)
- [ ] Task Manager app working
- [ ] Deployed to GitHub Pages or Vercel
- [ ] **React Fundamentals Badge** earned

---

<div align="center">

**Build modern UIs!** ⚛️

*Start with Module 01: Introduction to React*

</div>
