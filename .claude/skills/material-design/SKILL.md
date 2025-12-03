---
name: material-design
description: Create modern UI designs following Material Design 3 (M3) guidelines. Implements Dynamic Color, Typography, Elevation, Motion, and Components. Use when building M3-compliant interfaces in React, Vue, Flutter, Android, or Web.
---

# Material Design 3 Skill

Create beautiful, functional UIs based on Google's Material Design 3 (M3) guidelines.

## When to Use This Skill

- Creating M3-compliant UI components
- Implementing Dynamic Color system
- Applying M3 Typography, Elevation, Motion
- Building UIs in Android, Flutter, React, Vue, or Web
- Refactoring existing UIs to M3 style

---

## Core Design Principles

### Three Pillars of M3

1. **Personal**: Dynamic Color extracts colors from user's wallpaper for personalized experiences
2. **Adaptive**: Responds to various device sizes and form factors
3. **Expressive**: Bold colors and shapes express brand personality

---

## Color System

### Dynamic Color

Core M3 feature. Extracts colors from user's wallpaper and applies across the app.

### Color Roles

```
┌─────────────────────────────────────────────────────────────┐
│ Primary           │ Main actions, key elements              │
│ On Primary        │ Text/icons on Primary                   │
│ Primary Container │ Low-emphasis Primary variant            │
├─────────────────────────────────────────────────────────────┤
│ Secondary         │ Secondary actions, filters              │
│ On Secondary      │ Text/icons on Secondary                 │
│ Secondary Container│ Low-emphasis Secondary variant         │
├─────────────────────────────────────────────────────────────┤
│ Tertiary          │ Contrast, accents                       │
│ On Tertiary       │ Text/icons on Tertiary                  │
│ Tertiary Container│ Low-emphasis Tertiary variant           │
├─────────────────────────────────────────────────────────────┤
│ Error             │ Error states                            │
│ On Error          │ Text/icons on Error                     │
│ Error Container   │ Error background                        │
├─────────────────────────────────────────────────────────────┤
│ Surface           │ Backgrounds, cards, sheets              │
│ On Surface        │ Text/icons on Surface                   │
│ Surface Variant   │ Surface variation                       │
│ Outline           │ Borders, dividers                       │
│ Outline Variant   │ Low-emphasis borders                    │
└─────────────────────────────────────────────────────────────┘
```

### Tonal Palette

Each key color generates 13 tone values:

```
Tone:  0   10   20   30   40   50   60   70   80   90   95   99  100
       ■    ■    ■    ■    ■    ■    ■    ■    ■    ■    ■    ■    □
   Black←─────────────────────────────────────────────────────→White
```

### Color Tokens (CSS Variables)

```css
:root {
  /* Primary */
  --md-sys-color-primary: #6750A4;
  --md-sys-color-on-primary: #FFFFFF;
  --md-sys-color-primary-container: #EADDFF;
  --md-sys-color-on-primary-container: #21005D;

  /* Secondary */
  --md-sys-color-secondary: #625B71;
  --md-sys-color-on-secondary: #FFFFFF;
  --md-sys-color-secondary-container: #E8DEF8;
  --md-sys-color-on-secondary-container: #1D192B;

  /* Tertiary */
  --md-sys-color-tertiary: #7D5260;
  --md-sys-color-on-tertiary: #FFFFFF;
  --md-sys-color-tertiary-container: #FFD8E4;
  --md-sys-color-on-tertiary-container: #31111D;

  /* Error */
  --md-sys-color-error: #B3261E;
  --md-sys-color-on-error: #FFFFFF;
  --md-sys-color-error-container: #F9DEDC;
  --md-sys-color-on-error-container: #410E0B;

  /* Surface */
  --md-sys-color-surface: #FEF7FF;
  --md-sys-color-on-surface: #1D1B20;
  --md-sys-color-surface-variant: #E7E0EC;
  --md-sys-color-on-surface-variant: #49454F;

  /* Outline */
  --md-sys-color-outline: #79747E;
  --md-sys-color-outline-variant: #CAC4D0;

  /* Background */
  --md-sys-color-background: #FEF7FF;
  --md-sys-color-on-background: #1D1B20;
}
```

---

## Typography

### Type Scale

```
┌──────────────┬──────────┬─────────────┬────────┬──────────────┐
│ Role         │ Size     │ Line Height │ Weight │ Usage        │
├──────────────┼──────────┼─────────────┼────────┼──────────────┤
│ Display L    │ 57px     │ 64px        │ 400    │ Hero         │
│ Display M    │ 45px     │ 52px        │ 400    │ Large header │
│ Display S    │ 36px     │ 44px        │ 400    │ Medium header│
├──────────────┼──────────┼─────────────┼────────┼──────────────┤
│ Headline L   │ 32px     │ 40px        │ 400    │ Section      │
│ Headline M   │ 28px     │ 36px        │ 400    │ Subsection   │
│ Headline S   │ 24px     │ 32px        │ 400    │ Card header  │
├──────────────┼──────────┼─────────────┼────────┼──────────────┤
│ Title L      │ 22px     │ 28px        │ 400    │ Title        │
│ Title M      │ 16px     │ 24px        │ 500    │ Subtitle     │
│ Title S      │ 14px     │ 20px        │ 500    │ Small title  │
├──────────────┼──────────┼─────────────┼────────┼──────────────┤
│ Body L       │ 16px     │ 24px        │ 400    │ Body text    │
│ Body M       │ 14px     │ 20px        │ 400    │ Default text │
│ Body S       │ 12px     │ 16px        │ 400    │ Caption      │
├──────────────┼──────────┼─────────────┼────────┼──────────────┤
│ Label L      │ 14px     │ 20px        │ 500    │ Button       │
│ Label M      │ 12px     │ 16px        │ 500    │ Tab, chip    │
│ Label S      │ 11px     │ 16px        │ 500    │ Caption      │
└──────────────┴──────────┴─────────────┴────────┴──────────────┘
```

### Recommended Fonts

- **Display/Headline**: Roboto, Google Sans, system-ui
- **Body/Label**: Roboto, system-ui
- **Monospace**: Roboto Mono, Google Sans Mono

### Typography CSS Variables

```css
:root {
  /* Display */
  --md-sys-typescale-display-large: 400 57px/64px Roboto;
  --md-sys-typescale-display-medium: 400 45px/52px Roboto;
  --md-sys-typescale-display-small: 400 36px/44px Roboto;

  /* Headline */
  --md-sys-typescale-headline-large: 400 32px/40px Roboto;
  --md-sys-typescale-headline-medium: 400 28px/36px Roboto;
  --md-sys-typescale-headline-small: 400 24px/32px Roboto;

  /* Title */
  --md-sys-typescale-title-large: 400 22px/28px Roboto;
  --md-sys-typescale-title-medium: 500 16px/24px Roboto;
  --md-sys-typescale-title-small: 500 14px/20px Roboto;

  /* Body */
  --md-sys-typescale-body-large: 400 16px/24px Roboto;
  --md-sys-typescale-body-medium: 400 14px/20px Roboto;
  --md-sys-typescale-body-small: 400 12px/16px Roboto;

  /* Label */
  --md-sys-typescale-label-large: 500 14px/20px Roboto;
  --md-sys-typescale-label-medium: 500 12px/16px Roboto;
  --md-sys-typescale-label-small: 500 11px/16px Roboto;
}
```

---

## Elevation

### Levels and Usage

```
┌─────────┬────────────────────────────────────────────────────┐
│ Level   │ Usage                                              │
├─────────┼────────────────────────────────────────────────────┤
│ Level 0 │ Surface (same height as background)                │
│ Level 1 │ Card, Filled Button                                │
│ Level 2 │ Elevated Button, FAB (resting)                     │
│ Level 3 │ Navigation Drawer, Bottom Sheet                    │
│ Level 4 │ FAB (hover)                                        │
│ Level 5 │ Dialog, Modal                                      │
└─────────┴────────────────────────────────────────────────────┘
```

### Shadow + Surface Tint

M3 uses both Shadow and Surface Tint:

```css
.elevation-0 { box-shadow: none; }

.elevation-1 {
  box-shadow: 0px 1px 2px rgba(0, 0, 0, 0.3),
              0px 1px 3px 1px rgba(0, 0, 0, 0.15);
}

.elevation-2 {
  box-shadow: 0px 1px 2px rgba(0, 0, 0, 0.3),
              0px 2px 6px 2px rgba(0, 0, 0, 0.15);
}

.elevation-3 {
  box-shadow: 0px 1px 3px rgba(0, 0, 0, 0.3),
              0px 4px 8px 3px rgba(0, 0, 0, 0.15);
}

.elevation-4 {
  box-shadow: 0px 2px 3px rgba(0, 0, 0, 0.3),
              0px 6px 10px 4px rgba(0, 0, 0, 0.15);
}

.elevation-5 {
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.3),
              0px 8px 12px 6px rgba(0, 0, 0, 0.15);
}
```

---

## Motion

### Easing Curves

```
┌─────────────────┬────────────────────────────────────────────┐
│ Easing          │ CSS Value                                  │
├─────────────────┼────────────────────────────────────────────┤
│ Emphasized      │ cubic-bezier(0.2, 0, 0, 1)                │
│ Emphasized Dec. │ cubic-bezier(0.05, 0.7, 0.1, 1)           │
│ Emphasized Acc. │ cubic-bezier(0.3, 0, 0.8, 0.15)           │
│ Standard        │ cubic-bezier(0.2, 0, 0, 1)                │
│ Standard Dec.   │ cubic-bezier(0, 0, 0, 1)                  │
│ Standard Acc.   │ cubic-bezier(0.3, 0, 1, 1)                │
└─────────────────┴────────────────────────────────────────────┘
```

### Duration Tokens

```
┌─────────────────┬───────────┬──────────────────────────────┐
│ Token           │ Value     │ Usage                        │
├─────────────────┼───────────┼──────────────────────────────┤
│ Short 1         │ 50ms      │ Small icon changes           │
│ Short 2         │ 100ms     │ Switch, checkbox             │
│ Short 3         │ 150ms     │ Button state change          │
│ Short 4         │ 200ms     │ Chip, small card             │
├─────────────────┼───────────┼──────────────────────────────┤
│ Medium 1        │ 250ms     │ Card expand                  │
│ Medium 2        │ 300ms     │ Sheet display                │
│ Medium 3        │ 350ms     │ Modal display                │
│ Medium 4        │ 400ms     │ Page transition              │
├─────────────────┼───────────┼──────────────────────────────┤
│ Long 1          │ 450ms     │ Complex animation            │
│ Long 2          │ 500ms     │ Route transition             │
│ Long 3          │ 550ms     │ Large change                 │
│ Long 4          │ 600ms     │ Full screen transition       │
├─────────────────┼───────────┼──────────────────────────────┤
│ Extra Long 1-4  │ 700-1000ms│ Complex shared elements      │
└─────────────────┴───────────┴──────────────────────────────┘
```

### Motion CSS Variables

```css
:root {
  /* Easing */
  --md-sys-motion-easing-emphasized: cubic-bezier(0.2, 0, 0, 1);
  --md-sys-motion-easing-emphasized-decelerate: cubic-bezier(0.05, 0.7, 0.1, 1);
  --md-sys-motion-easing-emphasized-accelerate: cubic-bezier(0.3, 0, 0.8, 0.15);
  --md-sys-motion-easing-standard: cubic-bezier(0.2, 0, 0, 1);
  --md-sys-motion-easing-standard-decelerate: cubic-bezier(0, 0, 0, 1);
  --md-sys-motion-easing-standard-accelerate: cubic-bezier(0.3, 0, 1, 1);

  /* Duration */
  --md-sys-motion-duration-short1: 50ms;
  --md-sys-motion-duration-short2: 100ms;
  --md-sys-motion-duration-short3: 150ms;
  --md-sys-motion-duration-short4: 200ms;
  --md-sys-motion-duration-medium1: 250ms;
  --md-sys-motion-duration-medium2: 300ms;
  --md-sys-motion-duration-medium3: 350ms;
  --md-sys-motion-duration-medium4: 400ms;
}
```

---

## Shape

### Corner Radius

```
┌─────────────────┬───────────┬──────────────────────────────┐
│ Token           │ Value     │ Usage                        │
├─────────────────┼───────────┼──────────────────────────────┤
│ None            │ 0px       │ Sharp corners                │
│ Extra Small     │ 4px       │ Text field                   │
│ Small           │ 8px       │ Chip, menu                   │
│ Medium          │ 12px      │ Card, dialog                 │
│ Large           │ 16px      │ FAB, sheet                   │
│ Extra Large     │ 28px      │ Large sheet                  │
│ Full            │ 50%       │ Circular button, avatar      │
└─────────────────┴───────────┴──────────────────────────────┘
```

```css
:root {
  --md-sys-shape-corner-none: 0px;
  --md-sys-shape-corner-extra-small: 4px;
  --md-sys-shape-corner-small: 8px;
  --md-sys-shape-corner-medium: 12px;
  --md-sys-shape-corner-large: 16px;
  --md-sys-shape-corner-extra-large: 28px;
  --md-sys-shape-corner-full: 9999px;
}
```

---

## Components

### Buttons

```
┌─────────────────┬──────────────────────────────────────────┐
│ Type            │ Usage                                    │
├─────────────────┼──────────────────────────────────────────┤
│ Filled          │ Most important action (CTA)              │
│ Outlined        │ Medium emphasis action                   │
│ Text            │ Low priority, inline links               │
│ Elevated        │ Lower than Filled, needs depth           │
│ Tonal           │ Calmer than Filled, still important      │
└─────────────────┴──────────────────────────────────────────┘
```

### Button Implementation

```tsx
// React + Tailwind CSS
const FilledButton = ({ children, onClick }) => (
  <button
    onClick={onClick}
    className="
      h-10 px-6
      bg-primary text-on-primary
      rounded-full
      font-medium text-sm
      hover:shadow-md
      active:scale-[0.98]
      transition-all duration-150
    "
  >
    {children}
  </button>
);

const OutlinedButton = ({ children, onClick }) => (
  <button
    onClick={onClick}
    className="
      h-10 px-6
      bg-transparent text-primary
      border border-outline
      rounded-full
      font-medium text-sm
      hover:bg-primary/8
      active:scale-[0.98]
      transition-all duration-150
    "
  >
    {children}
  </button>
);

const TonalButton = ({ children, onClick }) => (
  <button
    onClick={onClick}
    className="
      h-10 px-6
      bg-secondary-container text-on-secondary-container
      rounded-full
      font-medium text-sm
      hover:shadow-sm
      active:scale-[0.98]
      transition-all duration-150
    "
  >
    {children}
  </button>
);
```

### Cards

```tsx
// Elevated Card
const ElevatedCard = ({ children }) => (
  <div className="
    p-4
    bg-surface-container-low
    rounded-xl
    shadow-elevation-1
    hover:shadow-elevation-2
    transition-shadow duration-200
  ">
    {children}
  </div>
);

// Filled Card
const FilledCard = ({ children }) => (
  <div className="
    p-4
    bg-surface-container-highest
    rounded-xl
  ">
    {children}
  </div>
);

// Outlined Card
const OutlinedCard = ({ children }) => (
  <div className="
    p-4
    bg-surface
    border border-outline-variant
    rounded-xl
  ">
    {children}
  </div>
);
```

### FAB (Floating Action Button)

```tsx
const FAB = ({ icon, onClick, variant = 'primary' }) => {
  const variants = {
    primary: 'bg-primary-container text-on-primary-container',
    secondary: 'bg-secondary-container text-on-secondary-container',
    tertiary: 'bg-tertiary-container text-on-tertiary-container',
    surface: 'bg-surface-container-high text-primary',
  };

  return (
    <button
      onClick={onClick}
      className={`
        w-14 h-14
        ${variants[variant]}
        rounded-lg
        shadow-elevation-3
        hover:shadow-elevation-4
        active:scale-[0.95]
        flex items-center justify-center
        transition-all duration-200
      `}
    >
      {icon}
    </button>
  );
};
```

### Navigation Bar

```tsx
const NavigationBar = ({ items, activeIndex, onChange }) => (
  <nav className="
    fixed bottom-0 left-0 right-0
    h-20 px-2
    bg-surface-container
    flex items-center justify-around
  ">
    {items.map((item, index) => (
      <button
        key={item.label}
        onClick={() => onChange(index)}
        className={`
          flex flex-col items-center gap-1
          px-4 py-2
          transition-all duration-200
          ${index === activeIndex
            ? 'text-on-secondary-container'
            : 'text-on-surface-variant'
          }
        `}
      >
        <div className={`
          w-16 h-8 rounded-full
          flex items-center justify-center
          transition-all duration-200
          ${index === activeIndex
            ? 'bg-secondary-container'
            : 'bg-transparent'
          }
        `}>
          {item.icon}
        </div>
        <span className="text-label-medium">{item.label}</span>
      </button>
    ))}
  </nav>
);
```

---

## Accessibility

### Color Contrast Requirements

- **Normal text**: 4.5:1 minimum (WCAG AA)
- **Large text**: 3:1 minimum
- **UI components**: 3:1 minimum

### Touch Targets

- **Minimum size**: 48x48dp
- **Recommended size**: 48x48dp or larger
- **Spacing**: 8dp minimum

### Focus Indicator

```css
:focus-visible {
  outline: 3px solid var(--md-sys-color-primary);
  outline-offset: 2px;
}
```

---

## Tailwind CSS Configuration

```javascript
// tailwind.config.js
module.exports = {
  theme: {
    extend: {
      colors: {
        primary: 'var(--md-sys-color-primary)',
        'on-primary': 'var(--md-sys-color-on-primary)',
        'primary-container': 'var(--md-sys-color-primary-container)',
        'on-primary-container': 'var(--md-sys-color-on-primary-container)',
        secondary: 'var(--md-sys-color-secondary)',
        'on-secondary': 'var(--md-sys-color-on-secondary)',
        'secondary-container': 'var(--md-sys-color-secondary-container)',
        'on-secondary-container': 'var(--md-sys-color-on-secondary-container)',
        tertiary: 'var(--md-sys-color-tertiary)',
        'on-tertiary': 'var(--md-sys-color-on-tertiary)',
        'tertiary-container': 'var(--md-sys-color-tertiary-container)',
        'on-tertiary-container': 'var(--md-sys-color-on-tertiary-container)',
        error: 'var(--md-sys-color-error)',
        'on-error': 'var(--md-sys-color-on-error)',
        'error-container': 'var(--md-sys-color-error-container)',
        'on-error-container': 'var(--md-sys-color-on-error-container)',
        surface: 'var(--md-sys-color-surface)',
        'on-surface': 'var(--md-sys-color-on-surface)',
        'surface-variant': 'var(--md-sys-color-surface-variant)',
        'on-surface-variant': 'var(--md-sys-color-on-surface-variant)',
        outline: 'var(--md-sys-color-outline)',
        'outline-variant': 'var(--md-sys-color-outline-variant)',
      },
      borderRadius: {
        'none': '0px',
        'xs': '4px',
        'sm': '8px',
        'md': '12px',
        'lg': '16px',
        'xl': '28px',
        'full': '9999px',
      },
      boxShadow: {
        'elevation-1': '0px 1px 2px rgba(0,0,0,0.3), 0px 1px 3px 1px rgba(0,0,0,0.15)',
        'elevation-2': '0px 1px 2px rgba(0,0,0,0.3), 0px 2px 6px 2px rgba(0,0,0,0.15)',
        'elevation-3': '0px 1px 3px rgba(0,0,0,0.3), 0px 4px 8px 3px rgba(0,0,0,0.15)',
        'elevation-4': '0px 2px 3px rgba(0,0,0,0.3), 0px 6px 10px 4px rgba(0,0,0,0.15)',
        'elevation-5': '0px 4px 4px rgba(0,0,0,0.3), 0px 8px 12px 6px rgba(0,0,0,0.15)',
      },
      transitionTimingFunction: {
        'emphasized': 'cubic-bezier(0.2, 0, 0, 1)',
        'emphasized-decelerate': 'cubic-bezier(0.05, 0.7, 0.1, 1)',
        'emphasized-accelerate': 'cubic-bezier(0.3, 0, 0.8, 0.15)',
      },
    },
  },
};
```

---

## Best Practices

### Do

- ✅ Use color roles appropriately (Primary = most important action)
- ✅ Express content hierarchy with consistent elevation
- ✅ Ensure touch targets are 48x48dp minimum
- ✅ Use appropriate easing and duration for animations
- ✅ Customize brand colors with Dynamic Color
- ✅ Follow accessibility contrast ratios

### Don't

- ❌ Ignore color roles and hardcode colors
- ❌ Overuse elevation without meaning
- ❌ Create touch targets that are too small
- ❌ Use animations that are too long or too short
- ❌ Use low-contrast color combinations
- ❌ Skip focus indicators

---

## AI Assistant Instructions

When this skill is invoked:

1. **Color**: Always use M3 color roles (Primary, Secondary, Surface, etc.)
2. **Typography**: Apply appropriate sizes and weights from Type Scale
3. **Elevation**: Choose levels based on content importance
4. **Motion**: Use proper easing and duration tokens
5. **Shape**: Apply appropriate corner radius for each component
6. **Accessibility**: Follow contrast ratios and touch target requirements

Always:
- Use CSS Variables for theme-ready code
- Consider dark mode support
- Apply responsive design principles

Never:
- Hardcode colors instead of using color roles
- Skip accessibility requirements
- Use arbitrary animation values

---

## Resources

- [Material Design 3 Official](https://m3.material.io/)
- [Material Theme Builder](https://www.figma.com/community/plugin/1034969338659738588)
- [Material Web Components](https://github.com/nicologhielmetti/material-design-icons)
- [Material Symbols](https://fonts.google.com/icons)
