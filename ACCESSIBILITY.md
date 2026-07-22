# Accessibility

```
Status: Draft
Priority: High
Owner: Repository Maintainer
Depends On: ENGINEERING_CONSTITUTION.md, PRINCIPLES.md, UI_UX_SPEC.md
Related Documents: DESIGN_SYSTEM.md, TESTING_STRATEGY.md
Next Expansion: Define per-component ARIA patterns and the accessibility test suite.
Last Updated: 2026-07-23
```

## Purpose
Ensure Dhee_AI is usable by everyone, including people using assistive technologies
(Accessibility First).

## Scope
Standards, patterns, and testing for all user-facing surfaces.

## Standard
Target **WCAG 2.2 Level AA** across the product.

## Requirements (design intent)
- **Keyboard:** full keyboard operability; visible focus; logical focus order; no keyboard traps.
- **Screen readers:** correct semantics, ARIA where needed, meaningful labels and announcements
  (including streaming updates).
- **Color & contrast:** meet AA contrast; never rely on color alone; support high-contrast and
  dark themes ([`DESIGN_SYSTEM.md`](DESIGN_SYSTEM.md)).
- **Motion:** respect reduced-motion preferences.
- **Forms & errors:** clear labels, instructions, and accessible error messaging.

## Testing
Automated accessibility checks in CI plus manual audits with assistive technology
([`TESTING_STRATEGY.md`](TESTING_STRATEGY.md), [`CI_CD.md`](CI_CD.md)). Accessibility is part of
the Definition of Done.
