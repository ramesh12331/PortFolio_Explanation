# 🧩 Component Architecture (Why This Structure)

```
App.jsx
 ├── Navbar
 ├── Banner
 ├── About
 ├── Services
 ├── Projects
 ├── Contact
 ├── Footer
 ├── SocialMedia
 └── ThemeContext
```

## Why this structure?

* Single Responsibility – each component does one job
* Reusable – components can be reused or reordered
* Scalable – easy to add new sections
* Readable – interviewers can understand instantly

### Architecture Talking Point

“Each UI section is isolated into its own component, making the app easy to maintain and scale.”

---

# 🧩 Component-by-Component Explanation (Interview Friendly)

## 1️⃣ App.jsx – Root Component

### What it does

* Manages theme state
* Applies theme class to `<html>`
* Wraps app with ThemeProvider
* Renders all major sections
* Configures ToastContainer

### Why it exists

* Central control point
* Global logic belongs here

### Key concepts used

* useState – themeMode
* useEffect – DOM updates & event listeners
* Context Provider

### Interview Answer

“App.jsx is the root component that manages global concerns like theme, layout composition, and notifications.”

---

## 2️⃣ Theme Context

### What it does

* Shares themeMode, darkTheme(), lightTheme() globally

### Why Context API

* Avoids prop drilling
* Simple global state (no Redux needed)

### How theme works

* Theme value updates
* `<html>` gets dark or light
* Tailwind `dark:` utilities respond

### Interview Answer

“Theme is global UI state, so Context API is the cleanest solution without extra libraries.”

---

## 3️⃣ Banner.jsx (Hero Section)

### What it does

* Shows greeting & name
* Typing animation effect
* Profile image
* Animated entrance

### Concepts used

* useState, useEffect
* setInterval with cleanup
* motion/react animations

### Important Interview Point

“I clean up intervals inside useEffect to avoid memory leaks.”

---

## 4️⃣ About.jsx (Tabbed Section)

### What it does

* Shows About content
* Tabs: Skills / Education / Experience
* Conditional rendering

### Why this approach

* Keeps DOM minimal
* Improves performance
* Easy to extend

### Interview Answer

“Tabs are controlled using state and conditional rendering to avoid unnecessary DOM updates.”

---

## 5️⃣ Services.jsx

### What it does

* Displays skill/service cards
* Uses icon components
* Hover interactions

### Why map() is used

* Data-driven UI
* Easy to add/remove services

### Interview Answer

“Services are rendered dynamically from an array, which makes the component scalable.”

---

## 6️⃣ Projects.jsx

### What it does

* Displays project cards
* Hover overlay with details
* External project links

### Key concepts

* map() rendering
* Unique keys
* Image hover effects

### Security point

* `rel="noopener noreferrer"` used for external links

---

## 7️⃣ Contact.jsx

### What it does

* Displays contact info
* Submits form using FormData
* Shows toast notifications

### Why FormData

* Simple for forms
* Supports file uploads

### Security awareness

* API key should be moved to backend/serverless

### Interview Answer

“For production, I’d proxy the form through a serverless function to secure API keys.”

---

## 8️⃣ Footer.jsx

### What it does

* Displays copyright
* Scroll-to-top button

### Concepts

* Scroll event listener
* Conditional rendering
* Smooth scrolling

---

## 9️⃣ SocialMedia.jsx

### What it does

* Floating social icons
* Dismissible panel

### UX consideration

* Doesn’t block content
* User can close it

---

# 🧠 Redux Store Design (Detailed)

## Did you use Redux?

No – intentionally.

### Why?

* App has simple UI state
* Context API is enough
* Redux would be over-engineering

## If Redux were added:

```
store
 ├── themeSlice
 ├── projectsSlice
 ├── uiSlice
```

### Interview Line

“Redux is best when state is complex or shared deeply; for this app, Context is simpler and cleaner.”
