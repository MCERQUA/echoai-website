# Echo AI Systems - CSS Architecture & Design System
*The visual language and styling foundation for Echo AI*

## 🎨 Design System Overview

### Core Philosophy
- **Dark-First**: Optimized for dark mode aesthetics
- **Fluid Typography**: Responsive text scaling
- **Motion Design**: Subtle animations enhance UX
- **Variable-Driven**: CSS custom properties for theming
- **Component Scoped**: Modular CSS architecture

## 🎯 CSS Architecture

### File Structure
```
dist/css/
├── reset.css          # Browser normalization
├── variables.css      # Design tokens & custom properties
├── base.css          # Global element styles
├── typography.css    # Text system
├── layout.css        # Grid & spacing utilities
├── components.css    # Reusable component styles
├── animations.css    # Animation library
├── utilities.css     # Helper classes
└── [page].css        # Page-specific styles
```

### Load Order
```html
<!-- Critical path CSS -->
<link rel="stylesheet" href="css/reset.css">
<link rel="stylesheet" href="css/variables.css">
<link rel="stylesheet" href="css/base.css">

<!-- Component styles -->
<link rel="stylesheet" href="css/components.css">

<!-- Enhancement styles -->
<link rel="stylesheet" href="css/animations.css">

<!-- Page-specific -->
<link rel="stylesheet" href="css/[page].css">
```

## 🌈 Color System

### Primary Palette
```css
:root {
  /* Brand Colors */
  --primary: #1a73e8;        /* Echo Blue */
  --primary-light: #4285f4;  /* Hover state */
  --primary-dark: #1557b0;   /* Active state */
  --primary-rgb: 26, 115, 232;
  
  /* Semantic Colors */
  --success: #34a853;        /* Green */
  --warning: #fbbc04;        /* Yellow */
  --danger: #ea4335;         /* Red */
  --info: #4285f4;          /* Light Blue */
  
  /* Neutral Scale */
  --gray-50: #f8f9fa;
  --gray-100: #f1f3f4;
  --gray-200: #e8eaed;
  --gray-300: #dadce0;
  --gray-400: #bdc1c6;
  --gray-500: #9aa0a6;
  --gray-600: #80868b;
  --gray-700: #5f6368;
  --gray-800: #3c4043;
  --gray-900: #202124;
  
  /* Dark Mode Base */
  --background: #0a0a0a;
  --surface: #1a1a1a;
  --surface-elevated: #242424;
  --border: #2a2a2a;
  
  /* Text Colors */
  --text-primary: #ffffff;
  --text-secondary: #a0a0a0;
  --text-muted: #666666;
  --text-disabled: #404040;
}
```

### Gradient System
```css
:root {
  /* Linear Gradients */
  --gradient-primary: linear-gradient(135deg, var(--primary) 0%, var(--primary-light) 100%);
  --gradient-dark: linear-gradient(180deg, #0a0a0a 0%, #1a1a1a 100%);
  --gradient-hero: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  
  /* Radial Gradients */
  --gradient-glow: radial-gradient(circle at center, rgba(26, 115, 232, 0.2) 0%, transparent 70%);
  --gradient-spotlight: radial-gradient(ellipse at top, #1a1a1a 0%, #0a0a0a 100%);
}
```

## 📐 Typography System

### Font Stack
```css
:root {
  /* Font Families */
  --font-sans: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  --font-mono: 'Fira Code', 'SF Mono', Monaco, monospace;
  --font-display: 'Outfit', var(--font-sans);
  
  /* Font Weights */
  --font-light: 300;
  --font-regular: 400;
  --font-medium: 500;
  --font-semibold: 600;
  --font-bold: 700;
  --font-black: 900;
}
```

### Type Scale
```css
:root {
  /* Fluid Typography - Mobile to Desktop */
  --text-xs: clamp(0.75rem, 0.7rem + 0.25vw, 0.875rem);
  --text-sm: clamp(0.875rem, 0.8rem + 0.375vw, 1rem);
  --text-base: clamp(1rem, 0.95rem + 0.25vw, 1.125rem);
  --text-lg: clamp(1.125rem, 1rem + 0.625vw, 1.25rem);
  --text-xl: clamp(1.25rem, 1.1rem + 0.75vw, 1.5rem);
  --text-2xl: clamp(1.5rem, 1.3rem + 1vw, 1.875rem);
  --text-3xl: clamp(1.875rem, 1.5rem + 1.875vw, 2.25rem);
  --text-4xl: clamp(2.25rem, 1.8rem + 2.25vw, 3rem);
  --text-5xl: clamp(3rem, 2.2rem + 4vw, 4rem);
  
  /* Line Heights */
  --leading-tight: 1.2;
  --leading-snug: 1.375;
  --leading-normal: 1.5;
  --leading-relaxed: 1.625;
  --leading-loose: 2;
}
```

### Typography Classes
```css
/* Headings */
.h1 {
  font-size: var(--text-5xl);
  font-weight: var(--font-bold);
  line-height: var(--leading-tight);
  font-family: var(--font-display);
}

.h2 {
  font-size: var(--text-4xl);
  font-weight: var(--font-semibold);
  line-height: var(--leading-tight);
}

/* Text Utilities */
.text-gradient {
  background: var(--gradient-primary);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.text-glow {
  text-shadow: 0 0 20px rgba(26, 115, 232, 0.5);
}
```

## 📏 Spacing System

### Space Scale
```css
:root {
  /* Base spacing unit = 4px */
  --space-1: 0.25rem;   /* 4px */
  --space-2: 0.5rem;    /* 8px */
  --space-3: 0.75rem;   /* 12px */
  --space-4: 1rem;      /* 16px */
  --space-5: 1.25rem;   /* 20px */
  --space-6: 1.5rem;    /* 24px */
  --space-8: 2rem;      /* 32px */
  --space-10: 2.5rem;   /* 40px */
  --space-12: 3rem;     /* 48px */
  --space-16: 4rem;     /* 64px */
  --space-20: 5rem;     /* 80px */
  --space-24: 6rem;     /* 96px */
  --space-32: 8rem;     /* 128px */
  
  /* Section spacing */
  --section-gap: clamp(3rem, 5vw, 6rem);
  --container-padding: clamp(1rem, 5vw, 3rem);
}
```

### Spacing Utilities
```css
/* Margin utilities */
.m-0 { margin: 0; }
.m-auto { margin: auto; }
.mx-auto { margin-left: auto; margin-right: auto; }
.mt-1 { margin-top: var(--space-1); }
.mr-2 { margin-right: var(--space-2); }
.mb-4 { margin-bottom: var(--space-4); }
.ml-8 { margin-left: var(--space-8); }

/* Padding utilities */
.p-0 { padding: 0; }
.p-4 { padding: var(--space-4); }
.px-4 { padding-left: var(--space-4); padding-right: var(--space-4); }
.py-8 { padding-top: var(--space-8); padding-bottom: var(--space-8); }
```

## 🏗️ Layout System

### Container
```css
.container {
  width: 100%;
  max-width: var(--container-max);
  margin-left: auto;
  margin-right: auto;
  padding-left: var(--container-padding);
  padding-right: var(--container-padding);
}

:root {
  --container-sm: 640px;
  --container-md: 768px;
  --container-lg: 1024px;
  --container-xl: 1280px;
  --container-2xl: 1536px;
  --container-max: 1440px;
}
```

### Grid System
```css
.grid {
  display: grid;
  gap: var(--space-4);
}

.grid-cols-1 { grid-template-columns: repeat(1, minmax(0, 1fr)); }
.grid-cols-2 { grid-template-columns: repeat(2, minmax(0, 1fr)); }
.grid-cols-3 { grid-template-columns: repeat(3, minmax(0, 1fr)); }
.grid-cols-4 { grid-template-columns: repeat(4, minmax(0, 1fr)); }
.grid-cols-auto { grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); }

/* Responsive grid */
@media (min-width: 768px) {
  .md\:grid-cols-2 { grid-template-columns: repeat(2, minmax(0, 1fr)); }
  .md\:grid-cols-3 { grid-template-columns: repeat(3, minmax(0, 1fr)); }
}
```

### Flexbox Utilities
```css
.flex { display: flex; }
.inline-flex { display: inline-flex; }

/* Direction */
.flex-row { flex-direction: row; }
.flex-col { flex-direction: column; }

/* Alignment */
.items-start { align-items: flex-start; }
.items-center { align-items: center; }
.items-end { align-items: flex-end; }

.justify-start { justify-content: flex-start; }
.justify-center { justify-content: center; }
.justify-end { justify-content: flex-end; }
.justify-between { justify-content: space-between; }

/* Wrapping */
.flex-wrap { flex-wrap: wrap; }
.flex-nowrap { flex-wrap: nowrap; }

/* Growth */
.flex-1 { flex: 1 1 0%; }
.flex-auto { flex: 1 1 auto; }
.flex-none { flex: none; }
```

## 💫 Animation System

### Timing Functions
```css
:root {
  /* Easing curves */
  --ease-linear: linear;
  --ease-in: cubic-bezier(0.4, 0, 1, 1);
  --ease-out: cubic-bezier(0, 0, 0.2, 1);
  --ease-in-out: cubic-bezier(0.4, 0, 0.2, 1);
  --ease-bounce: cubic-bezier(0.68, -0.55, 0.265, 1.55);
  
  /* Durations */
  --duration-fast: 150ms;
  --duration-base: 300ms;
  --duration-slow: 500ms;
  --duration-slower: 1000ms;
}
```

### Keyframe Animations
```css
@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

@keyframes slideUp {
  from { 
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes pulse {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.5; }
}

@keyframes spin {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

@keyframes gradient-shift {
  0% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
}
```

### Animation Classes
```css
.animate-fadeIn {
  animation: fadeIn var(--duration-base) var(--ease-out);
}

.animate-slideUp {
  animation: slideUp var(--duration-base) var(--ease-out);
}

.animate-pulse {
  animation: pulse 2s var(--ease-in-out) infinite;
}

.animate-spin {
  animation: spin 1s var(--ease-linear) infinite;
}

.animate-gradient {
  background-size: 200% 200%;
  animation: gradient-shift 3s ease infinite;
}
```

## 🎭 Component Styling

### Card Component
```css
.card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: var(--radius-lg);
  padding: var(--space-6);
  transition: all var(--duration-base) var(--ease-out);
}

.card:hover {
  transform: translateY(-4px);
  box-shadow: var(--shadow-xl);
  border-color: var(--primary);
}

.card-glow {
  position: relative;
}

.card-glow::before {
  content: '';
  position: absolute;
  inset: -2px;
  background: var(--gradient-primary);
  border-radius: var(--radius-lg);
  opacity: 0;
  transition: opacity var(--duration-base);
  z-index: -1;
  filter: blur(10px);
}

.card-glow:hover::before {
  opacity: 0.5;
}
```

### Button Component
```css
.btn {
  --btn-height: 2.75rem;
  --btn-padding: 0 1.5rem;
  --btn-font-size: var(--text-base);
  
  display: inline-flex;
  align-items: center;
  justify-content: center;
  height: var(--btn-height);
  padding: var(--btn-padding);
  font-size: var(--btn-font-size);
  font-weight: var(--font-medium);
  border-radius: var(--radius-md);
  transition: all var(--duration-fast) var(--ease-out);
  cursor: pointer;
  position: relative;
  overflow: hidden;
}

.btn-primary {
  background: var(--gradient-primary);
  color: white;
  border: none;
}

.btn-primary::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(45deg, transparent 30%, rgba(255,255,255,0.2) 50%, transparent 70%);
  transform: translateX(-100%);
  transition: transform 0.6s;
}

.btn-primary:hover::before {
  transform: translateX(100%);
}
```

## 🌙 Dark Mode Variables

### Automatic Dark Mode
```css
@media (prefers-color-scheme: dark) {
  :root {
    --background: #0a0a0a;
    --surface: #1a1a1a;
    --surface-elevated: #242424;
    --border: #2a2a2a;
    --text-primary: #ffffff;
    --text-secondary: #a0a0a0;
  }
}

/* Manual dark mode toggle */
[data-theme="dark"] {
  --background: #0a0a0a;
  --surface: #1a1a1a;
  /* ... rest of dark theme */
}

[data-theme="light"] {
  --background: #ffffff;
  --surface: #f8f9fa;
  /* ... rest of light theme */
}
```

## 📱 Responsive Utilities

### Breakpoint System
```css
:root {
  --breakpoint-sm: 640px;
  --breakpoint-md: 768px;
  --breakpoint-lg: 1024px;
  --breakpoint-xl: 1280px;
  --breakpoint-2xl: 1536px;
}

/* Mobile-first responsive utilities */
.hidden { display: none; }
.block { display: block; }
.inline-block { display: inline-block; }

@media (min-width: 768px) {
  .md\:hidden { display: none; }
  .md\:block { display: block; }
  .md\:flex { display: flex; }
  .md\:grid { display: grid; }
}

@media (min-width: 1024px) {
  .lg\:hidden { display: none; }
  .lg\:block { display: block; }
  .lg\:flex { display: flex; }
}
```

## 🛡️ CSS Variables Reference

### Shadows
```css
:root {
  --shadow-sm: 0 1px 2px 0 rgba(0, 0, 0, 0.05);
  --shadow-md: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
  --shadow-lg: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
  --shadow-xl: 0 20px 25px -5px rgba(0, 0, 0, 0.1);
  --shadow-2xl: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
  --shadow-inner: inset 0 2px 4px 0 rgba(0, 0, 0, 0.06);
}
```

### Border Radius
```css
:root {
  --radius-none: 0;
  --radius-sm: 0.125rem;
  --radius-md: 0.375rem;
  --radius-lg: 0.5rem;
  --radius-xl: 0.75rem;
  --radius-2xl: 1rem;
  --radius-full: 9999px;
}
```

### Z-Index Scale
```css
:root {
  --z-below: -1;
  --z-base: 0;
  --z-dropdown: 10;
  --z-sticky: 20;
  --z-overlay: 30;
  --z-modal: 40;
  --z-popover: 50;
  --z-tooltip: 60;
  --z-notification: 70;
  --z-maximum: 9999;
}
```

---
*Design System v2.0 - Engineered for dark mode excellence*