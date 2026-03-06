# STYLEGUIDE — Design System

Shared design rules for Designer and Engineer agents.

## Theme

- Clean SaaS, light theme by default
- Dark mode support via `class` strategy

## Colors

Use CSS custom properties defined in `globals.css`:

```
--background, --foreground
--primary, --primary-foreground
--secondary, --muted, --accent
--destructive, --border, --input, --ring
```

Never use hardcoded hex values. Always use tokens.

## Typography

- Font: system sans-serif (Inter or Geist if available)
- Body: 14-16px
- Headings: Tailwind `text-xl` to `text-4xl`
- Monospace: JetBrains Mono for code

## Components

- Use shadcn/ui from `components/ui/*`
- Conditional styles via `cn()` utility
- All buttons/inputs must have: hover, focus, disabled states
- Border radius: `rounded-lg` (default), `rounded-xl` for cards

## Spacing

- Follow 4px grid (Tailwind default spacing)
- Section padding: `py-12` to `py-20`
- Card padding: `p-4` to `p-6`

## Responsive

- Mobile-first approach
- Breakpoints: `sm:640` `md:768` `lg:1024` `xl:1280`
- Test all features at 375px width

## Accessibility

- Minimum AA contrast
- `aria-label` for icon-only buttons
- Logical tab order
- Error states: text + color (not color alone)

## Don'ts

- No inline styles
- No random shadows/gradients without purpose
- No mixing accent colors without tokens
- No walls of text in UI
