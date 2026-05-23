# Icon Design

Use this guide to choose icons that are consistent, semantic, accessible, and easy to maintain.

## Priority order
1. Follow the product’s existing design system first.
2. Use this guide second.
3. If the icon is still unclear, choose the simplest semantic icon instead of a decorative one.
4. Do not invent a new icon pattern when an existing one already fits.

## Default rules
- Prefer **Lucide** for React projects.
- Use **explicit named imports only**.
- Never use emoji as UI icons.
- Keep one icon style per section: **outline or solid**, not both.
- Use **semantic Tailwind colors** only.
- Make icons inherit color from text using `currentColor`.
- Keep icon sizing consistent within the same visual block.

---

# Quick icon mapping

Use these icons as the default match for common concepts.

| Concept | Lucide | Heroicons | Phosphor |
|---------|--------|-----------|----------|
| Award / Quality | `Trophy` | `trophy` | `Trophy` |
| Price / Value | `Tag` | `tag` | `Tag` |
| Location | `MapPin` | `map-pin` | `MapPin` |
| Expertise / Education | `GraduationCap` | `academic-cap` | `GraduationCap` |
| Support / Chat | `MessageCircle` | `chat-bubble-left-right` | `ChatCircle` |
| Security / Trust | `Shield` | `shield-check` | `Shield` |
| Speed / Action | `Zap` | `bolt` | `Lightning` |
| Phone | `Phone` | `phone` | `Phone` |
| Email | `Mail` | `envelope` | `Envelope` |
| User / Profile | `User` | `user` | `User` |
| Team | `Users` | `user-group` | `Users` |
| Settings | `Settings` | `cog-6-tooth` | `Gear` |
| Home | `Home` | `home` | `House` |
| Search | `Search` | `magnifying-glass` | `MagnifyingGlass` |
| Success / Check | `Check` | `check` | `Check` |
| Close / Cancel | `X` | `x-mark` | `X` |
| Menu | `Menu` | `bars-3` | `List` |
| Calendar | `Calendar` | `calendar` | `Calendar` |
| Clock / Time | `Clock` | `clock` | `Clock` |
| Favorite / Like | `Heart` | `heart` | `Heart` |

---

# Library choice

Use the library that best matches the project, but keep the style consistent.

| Library | Best for | Package |
|---------|----------|---------|
| Lucide | General use, React projects | `lucide-react` |
| Heroicons | Tailwind-first interfaces | `@heroicons/react` |
| Phosphor | When weight variations matter | `@phosphor-icons/react` |

**Default recommendation:** Lucide. It has a large icon set, works cleanly with React, and is the safest default for most UI work.

---

# Selection process

1. Read the label and understand the concept.
2. Pick the semantic meaning first, not the visual shape.
3. Check the mapping table or semantic references.
4. Choose the default icon from the preferred library.
5. Verify style consistency with nearby icons.
6. Use the fallback rules only when the meaning is broad or ambiguous.

---

# Fallback rules

When the icon is not obvious, use the most neutral semantic option.

- Generic success or approval → `CheckCircle`
- Generic feature or enhancement → `Sparkles`
- Generic information → `Info`
- Generic warning → `AlertTriangle`
- Generic action → `ArrowRight`

Only ask for clarification when the icon changes the meaning of the UI.

---

# Sizing rules

Use the same size for similar icons in the same section.

| Context | Tailwind class | Pixel range |
|---------|----------------|-------------|
| Inline with text | `w-4 h-4` or `w-5 h-5` | 16–20px |
| Feature cards | `w-6 h-6` to `w-8 h-8` | 24–32px |
| Hero sections | `w-10 h-10` to `w-12 h-12` | 40–48px |
| Decorative large | `w-16 h-16` | 64px |

---

# Color rules

- Use `text-primary` for normal emphasis.
- Use `text-muted-foreground` for secondary meaning.
- Use `text-destructive` for errors and warnings.
- Never hardcode raw hex or arbitrary blue/gray values for icons when semantic tokens exist.

---

# Accessibility rules

- Decorative icons should be hidden from assistive tech with `aria-hidden="true"`.
- Icon-only buttons must always have an `aria-label`.
- Standalone meaningful icons should have a label or surrounding text.
- Do not rely on color alone to communicate meaning.

---

# Tree-shaking rules

Do not access icons dynamically.

Use explicit imports so bundlers can remove unused icons.

## Correct

```tsx
import { Home, Users, Settings, type LucideIcon } from 'lucide-react'

const ICON_MAP: Record<string, LucideIcon> = {
  home: Home,
  users: Users,
  settings: Settings,
}

const Icon = ICON_MAP[iconName]

if (!Icon) {
  throw new Error(`Unknown icon: ${iconName}`)
}