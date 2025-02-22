Below is a common folder structure you can use for an Atomic Design–based React + TypeScript project. This setup makes it easy to scale your components, keep everything organized, and integrate Storybook.

---

## Recommended Folder Structure

```
nodebox/
├─ .storybook/           // Storybook config files (optional if using Storybook)
├─ public/               // Static assets, favicon, index.html, etc.
├─ src/
│  ├─ components/
│  │  ├─ atoms/
│  │  │  ├─ Button/
│  │  │  │  ├─ Button.tsx
│  │  │  │  ├─ Button.stories.tsx   // Storybook stories for Button
│  │  │  │  ├─ Button.test.tsx      // Tests for Button
│  │  │  │  └─ index.ts             // Export the Button component
│  │  │  └─ (other atoms)/
│  │  ├─ molecules/
│  │  │  └─ (your molecule components)/
│  │  ├─ organisms/
│  │  │  └─ (your organism components)/
│  │  ├─ templates/
│  │  │  └─ (your template components)/
│  │  └─ pages/
│  │     └─ (your page components)/
│  ├─ theme/
│  │  ├─ index.ts         // Exports your theme object (colors, spacing, etc.)
│  │  └─ styled.d.ts      // Type definitions for styled-components theme
│  ├─ App.tsx             // Root component
│  ├─ index.tsx           // Renders <App />, ReactDOM entry point
│  └─ globalStyles.css    // If you have any global CSS or resets (optional)
├─ package.json
├─ tsconfig.json
└─ ... (other config files)
```

### Key Points About This Structure

1. **`components/` Folder**  
   - Break down by Atomic Design: `atoms`, `molecules`, `organisms`, `templates`, and `pages`.  
   - Each component gets its own folder (e.g., `Button/`), making it easier to keep related files (stories, tests, styles) together.

2. **`theme/` Folder**  
   - Holds your design tokens (colors, spacing, typography) in a single `index.ts`.  
   - The `styled.d.ts` file extends `DefaultTheme` from `styled-components` so TypeScript knows about your custom theme.

3. **Storybook Files (`.storybook/` Folder)**  
   - If you’re using Storybook, you’ll likely have `main.js`, `preview.js` (or `preview.ts`), and other config files in a dedicated `.storybook` folder.  
   - Inside each component folder, you can have a `ComponentName.stories.tsx` file for your stories.

4. **Testing Files**  
   - You can place tests (e.g., `Button.test.tsx`) in the same folder as the component or in a dedicated `__tests__` folder. Co-locating tests with components is popular because it keeps everything about a component in one place.

5. **Global Styles**  
   - If you have a global CSS reset or styles that apply to the entire app, you can keep them in `globalStyles.css` (or a similar naming convention). Alternatively, you could manage global styles with styled-components’ `createGlobalStyle`.

6. **`index.tsx`**  
   - The main entry point where ReactDOM (or another rendering library) mounts your `<App />`.

7. **`App.tsx`**  
   - The root component that might wrap everything in a `ThemeProvider` or contain top-level routes.

---

### Example: Button Folder Structure

```plaintext
atoms/
└─ Button/
   ├─ Button.tsx           // The Button component
   ├─ Button.stories.tsx   // Storybook stories
   ├─ Button.test.tsx      // Jest + React Testing Library tests
   └─ index.ts             // `export { default as Button } from './Button';`
```

Then, in `atoms/index.ts`, you could export all atom components:

```typescript
export * from './Button';
export * from './Input';
...
```
