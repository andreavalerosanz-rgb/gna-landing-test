# GNA Hotel Solutions - Frontend Technical Test

A fully responsive, modern landing page built as a technical assignment for GNA Hotel Solutions. The project focuses on clean architecture, performance optimization, and pixel-perfect design matching the provided Figma mockups.

## 🚀 Live Demo


## 🛠️ Tech Stack
* **Framework:** Vue 3 (Composition API / `<script setup>`)
* **Styling:** Tailwind CSS
* **Build Tool:** Vite

## 🧠 Architectural Decisions & Highlights
1. **Component-Driven Design:** The UI is broken down into modular, reusable components. For example, the project section utilizes a "Smart/Dumb" component architecture:
   * `ArticleSection.vue` (Smart): Manages state, handles filtering logic, and iterates over the data.
   * `ArticleCard.vue` (Dumb): Purely presentational, receives data via `props`, and automatically handles the alternating "zig-zag" layout based on its index.
2. **Optimized Reactivity:** The filtering system is powered by Vue's `computed` properties. The filtered array is cached and only recalculates when the filter state changes, avoiding unnecessary re-renders and improving performance.
3. **Mobile-First & Responsive:** The layout seamlessly adapts from mobile screens (using native collapse menus) to large desktop displays (using specific `md:` and `lg:` breakpoints) without relying on heavy external UI libraries.
4. **Optical Alignment:** Special attention was given to typography and optical alignment using targeted CSS utility classes (like `origin-top-left` and `scale`) to perfectly match the design specifications.

## ⚙️ Project Setup

### Prerequisites
Make sure you have Node.js installed on your machine.

### Installation
Clone the repository and install the dependencies:

npm install

### Development Server
Run the local development server (usually at http://localhost:5173):
npm run dev

### Production Build
Compile and minify the project for production:
npm run build

**Developed by Andrea Valero Sanz**