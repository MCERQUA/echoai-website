# Echo AI Systems - Frontend Component Library
*Reusable UI components and patterns for the Echo ecosystem*

## 🎨 Component Overview

### Design Philosophy
- **Modular**: Each component is self-contained
- **Accessible**: WCAG 2.1 AA compliant
- **Responsive**: Mobile-first design
- **Performant**: Optimized for speed
- **Themeable**: CSS custom properties

## 📦 Core Components

### Navigation Components

#### MainNav
Primary navigation component with mobile responsiveness.

```html
<nav class="main-nav" data-component="main-nav">
  <div class="nav-brand">
    <img src="/images/logo.svg" alt="Echo AI">
  </div>
  <ul class="nav-menu">
    <li><a href="#services">Services</a></li>
    <li><a href="#about">About</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
  <button class="nav-toggle" aria-label="Menu">
    <span></span>
  </button>
</nav>
```

**JavaScript:**
```javascript
import { MainNav } from './components/navigation.js';

const nav = new MainNav({
  sticky: true,
  scrollThreshold: 100,
  mobileBreakpoint: 768
});
```

#### TabNav
Tabbed navigation for content sections.

```html
<div class="tab-nav" data-component="tab-nav">
  <div class="tab-buttons">
    <button class="tab-btn active" data-tab="overview">Overview</button>
    <button class="tab-btn" data-tab="details">Details</button>
  </div>
  <div class="tab-content">
    <div id="overview" class="tab-pane active">Content</div>
    <div id="details" class="tab-pane">Content</div>
  </div>
</div>
```

### Card Components

#### ServiceCard
Service presentation card with hover effects.

```html
<div class="service-card" data-component="service-card">
  <div class="card-icon">
    <i class="fas fa-rocket"></i>
  </div>
  <h3 class="card-title">Service Title</h3>
  <p class="card-description">Service description</p>
  <ul class="card-features">
    <li>Feature 1</li>
    <li>Feature 2</li>
  </ul>
  <a href="#" class="card-cta btn btn-primary">Learn More</a>
</div>
```

**CSS Variables:**
```css
.service-card {
  --card-bg: var(--surface);
  --card-border: var(--border-color);
  --card-shadow: var(--shadow-md);
  --card-radius: var(--radius-lg);
}
```

#### StatsCard
Animated statistics display card.

```html
<div class="stats-card" data-component="stats-card">
  <div class="stat-value" data-count="500">0</div>
  <div class="stat-label">Happy Clients</div>
  <div class="stat-icon">
    <i class="fas fa-users"></i>
  </div>
</div>
```

**JavaScript:**
```javascript
import { StatsCounter } from './components/animations.js';

const counter = new StatsCounter({
  duration: 2000,
  easing: 'easeOutQuart',
  separator: ','
});
```

### Form Components

#### InputField
Enhanced input with validation and feedback.

```html
<div class="input-field" data-component="input-field">
  <label for="email">Email Address</label>
  <input 
    type="email" 
    id="email" 
    name="email"
    required
    data-validate="email"
  >
  <span class="error-message"></span>
  <span class="success-icon">✓</span>
</div>
```

**Validation Rules:**
```javascript
const validationRules = {
  email: /^[^\s@]+@[^\s@]+\.[^\s@]+$/,
  phone: /^\d{3}-\d{3}-\d{4}$/,
  url: /^https?:\/\/.+\..+/,
  required: value => value.trim().length > 0
};
```

#### SelectDropdown
Custom styled select with search.

```html
<div class="select-dropdown" data-component="select-dropdown">
  <button class="select-trigger">
    <span class="select-value">Choose Option</span>
    <i class="fas fa-chevron-down"></i>
  </button>
  <div class="select-options">
    <input type="search" placeholder="Search...">
    <ul>
      <li data-value="1">Option 1</li>
      <li data-value="2">Option 2</li>
    </ul>
  </div>
</div>
```

### Modal Components

#### BaseModal
Reusable modal dialog system.

```html
<div class="modal" data-component="modal" id="example-modal">
  <div class="modal-backdrop"></div>
  <div class="modal-content">
    <div class="modal-header">
      <h2 class="modal-title">Modal Title</h2>
      <button class="modal-close">&times;</button>
    </div>
    <div class="modal-body">
      <!-- Content -->
    </div>
    <div class="modal-footer">
      <button class="btn btn-secondary" data-dismiss="modal">Cancel</button>
      <button class="btn btn-primary">Confirm</button>
    </div>
  </div>
</div>
```

**JavaScript API:**
```javascript
import { Modal } from './components/modal.js';

const modal = new Modal('#example-modal');

// Open modal
modal.open();

// Close modal
modal.close();

// Listen to events
modal.on('open', () => console.log('Modal opened'));
modal.on('close', () => console.log('Modal closed'));
```

### Loading Components

#### Spinner
Configurable loading spinner.

```html
<div class="spinner" data-component="spinner">
  <div class="spinner-circle"></div>
</div>
```

**Variants:**
```html
<!-- Sizes -->
<div class="spinner spinner-sm"></div>
<div class="spinner spinner-md"></div>
<div class="spinner spinner-lg"></div>

<!-- Colors -->
<div class="spinner spinner-primary"></div>
<div class="spinner spinner-success"></div>
<div class="spinner spinner-warning"></div>
```

#### ProgressBar
Animated progress indicator.

```html
<div class="progress-bar" data-component="progress-bar">
  <div class="progress-track">
    <div class="progress-fill" data-progress="75">
      <span class="progress-label">75%</span>
    </div>
  </div>
</div>
```

### Alert Components

#### Toast
Non-blocking notification system.

```html
<div class="toast" data-component="toast">
  <div class="toast-icon">
    <i class="fas fa-check-circle"></i>
  </div>
  <div class="toast-content">
    <div class="toast-title">Success!</div>
    <div class="toast-message">Operation completed</div>
  </div>
  <button class="toast-close">&times;</button>
</div>
```

**JavaScript Usage:**
```javascript
import { Toast } from './components/toast.js';

Toast.success('Operation completed!');
Toast.error('Something went wrong');
Toast.warning('Please check your input');
Toast.info('Did you know?');
```

### Button Components

#### Button
Versatile button with multiple variants.

```html
<!-- Primary -->
<button class="btn btn-primary">Primary Button</button>

<!-- Secondary -->
<button class="btn btn-secondary">Secondary Button</button>

<!-- Outline -->
<button class="btn btn-outline">Outline Button</button>

<!-- Sizes -->
<button class="btn btn-sm">Small</button>
<button class="btn btn-md">Medium</button>
<button class="btn btn-lg">Large</button>

<!-- States -->
<button class="btn btn-primary" disabled>Disabled</button>
<button class="btn btn-loading">
  <span class="spinner"></span>
  Loading...
</button>
```

### Grid Components

#### ResponsiveGrid
Flexible grid system.

```html
<div class="grid" data-columns="auto">
  <div class="grid-item">Item 1</div>
  <div class="grid-item">Item 2</div>
  <div class="grid-item">Item 3</div>
</div>
```

**CSS Grid Classes:**
```css
.grid-1 { grid-template-columns: 1fr; }
.grid-2 { grid-template-columns: repeat(2, 1fr); }
.grid-3 { grid-template-columns: repeat(3, 1fr); }
.grid-4 { grid-template-columns: repeat(4, 1fr); }
.grid-auto { grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); }
```

## 🎯 Component Patterns

### Lazy Loading Pattern
```javascript
class LazyComponent {
  constructor(selector) {
    this.elements = document.querySelectorAll(selector);
    this.observer = new IntersectionObserver(this.onIntersect.bind(this));
    this.observe();
  }
  
  observe() {
    this.elements.forEach(el => this.observer.observe(el));
  }
  
  onIntersect(entries) {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        this.loadComponent(entry.target);
        this.observer.unobserve(entry.target);
      }
    });
  }
  
  loadComponent(element) {
    // Load component logic
  }
}
```

### Event Delegation Pattern
```javascript
class ComponentManager {
  constructor(container) {
    this.container = container;
    this.attachEventListeners();
  }
  
  attachEventListeners() {
    this.container.addEventListener('click', (e) => {
      const component = e.target.closest('[data-component]');
      if (component) {
        this.handleComponentAction(component, e);
      }
    });
  }
  
  handleComponentAction(component, event) {
    const type = component.dataset.component;
    const action = event.target.dataset.action;
    
    switch(type) {
      case 'modal':
        this.handleModal(action, component);
        break;
      case 'tab-nav':
        this.handleTabNav(action, component);
        break;
    }
  }
}
```

## 🛠️ Component Utilities

### DOM Utilities
```javascript
// Query utilities
const $ = (selector, context = document) => context.querySelector(selector);
const $$ = (selector, context = document) => [...context.querySelectorAll(selector)];

// Class utilities
const addClass = (el, className) => el.classList.add(className);
const removeClass = (el, className) => el.classList.remove(className);
const toggleClass = (el, className) => el.classList.toggle(className);
const hasClass = (el, className) => el.classList.contains(className);

// Attribute utilities
const attr = (el, name, value) => {
  if (value === undefined) return el.getAttribute(name);
  el.setAttribute(name, value);
};
```

### Animation Utilities
```javascript
// Fade animations
const fadeIn = (element, duration = 300) => {
  element.style.opacity = 0;
  element.style.display = 'block';
  
  const start = performance.now();
  
  const animate = (timestamp) => {
    const elapsed = timestamp - start;
    const progress = Math.min(elapsed / duration, 1);
    
    element.style.opacity = progress;
    
    if (progress < 1) {
      requestAnimationFrame(animate);
    }
  };
  
  requestAnimationFrame(animate);
};

// Slide animations
const slideDown = (element, duration = 300) => {
  element.style.overflow = 'hidden';
  const height = element.scrollHeight;
  element.style.height = 0;
  
  const start = performance.now();
  
  const animate = (timestamp) => {
    const elapsed = timestamp - start;
    const progress = Math.min(elapsed / duration, 1);
    
    element.style.height = `${height * progress}px`;
    
    if (progress < 1) {
      requestAnimationFrame(animate);
    } else {
      element.style.height = '';
      element.style.overflow = '';
    }
  };
  
  requestAnimationFrame(animate);
};
```

## 📱 Responsive Utilities

### Breakpoint Manager
```javascript
const Breakpoints = {
  mobile: 768,
  tablet: 1024,
  desktop: 1440,
  
  isMobile: () => window.innerWidth < Breakpoints.mobile,
  isTablet: () => window.innerWidth >= Breakpoints.mobile && window.innerWidth < Breakpoints.desktop,
  isDesktop: () => window.innerWidth >= Breakpoints.desktop,
  
  onResize: (callback) => {
    let timeout;
    window.addEventListener('resize', () => {
      clearTimeout(timeout);
      timeout = setTimeout(callback, 100);
    });
  }
};
```

## 🎭 Accessibility Utilities

### ARIA Helpers
```javascript
const A11y = {
  announce: (message) => {
    const announcement = document.createElement('div');
    announcement.setAttribute('aria-live', 'polite');
    announcement.setAttribute('aria-atomic', 'true');
    announcement.style.position = 'absolute';
    announcement.style.left = '-10000px';
    announcement.textContent = message;
    document.body.appendChild(announcement);
    setTimeout(() => announcement.remove(), 1000);
  },
  
  trapFocus: (element) => {
    const focusable = element.querySelectorAll(
      'a[href], button, textarea, input, select, [tabindex]:not([tabindex="-1"])'
    );
    const first = focusable[0];
    const last = focusable[focusable.length - 1];
    
    element.addEventListener('keydown', (e) => {
      if (e.key === 'Tab') {
        if (e.shiftKey && document.activeElement === first) {
          e.preventDefault();
          last.focus();
        } else if (!e.shiftKey && document.activeElement === last) {
          e.preventDefault();
          first.focus();
        }
      }
    });
  }
};
```

## 🚀 Component Best Practices

1. **Single Responsibility**: Each component does one thing well
2. **Data Attributes**: Use data-* attributes for JavaScript hooks
3. **CSS Modules**: Scope styles to avoid conflicts
4. **Progressive Enhancement**: Components work without JavaScript
5. **Event Cleanup**: Remove listeners when components unmount
6. **Error Boundaries**: Handle component errors gracefully
7. **Performance**: Use requestAnimationFrame for animations
8. **Accessibility**: Include ARIA labels and keyboard navigation

---
*Component library version 2.0 - January 2025*