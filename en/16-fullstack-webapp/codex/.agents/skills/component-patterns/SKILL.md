---
name: component-patterns
description: >-
  Trigger when: the task needs `component-patterns` guidance as a focused standalone step or as part of the `fullstack-webapp` harness. Do not trigger when: the user wants the full `fullstack-webapp` pipeline or an unrelated task outside this skill's domain. Expected input: brief, draft, issue, or source material. Expected output: domain-specific guidance, patterns, checks, or revisions.
---

A reference for component patterns, state management strategies, and project structure that the frontend-dev agent uses during frontend development.

## Target Agent

`frontend-dev` — Applies this skill's patterns directly to component design and state management.

## Component Design Patterns

### 1. Compound Components
A pattern where parent and child share implicit state.

**Suited for**: Tab, Accordion, Dropdown, Select, and other composite UI
**Structure**: `<Select>` + `<Select.Trigger>` + `<Select.Option>`
**Key Concept**: State sharing via Context, flexible composition through children

### 2. Render Props / Children as Function
Delegates rendering logic externally.

**Suited for**: Data fetching wrappers, mouse/scroll tracking
**Structure**: `<DataLoader render={(data) => <UI data={data} />} />`
**Note**: Prefer Hook pattern when it can replace this

### 3. Custom Hooks (Extraction Pattern)
Extracts state logic into reusable Hooks.

**Suited for**: Form management, API calls, localStorage, debounce
**Naming**: `use` prefix required — `useForm`, `useDebounce`, `useAuth`

### 4. Container/Presentational Separation
Separates data logic (Container) from UI presentation (Presentational).

**Suited for**: Large-scale apps, when testability is needed
**Container**: Data fetch, state management, event handlers
**Presentational**: Renders only from props, functionally pure

### 5. Higher-Order Component (HOC)
Wraps a component to add functionality.

**Suited for**: Auth guards, layout wrappers, error boundaries
**Naming**: `with` prefix — `withAuth`, `withLayout`
**Note**: Prefer Hook/Context when they can replace this

### 6. Headless Component
Provides behavior/state without UI.

**Suited for**: Sharing logic independent of design system
**Examples**: headless `useCombobox`, `useDialog`, `useTable`

## State Management Strategy Selection Guide

| State Type | Recommended Tool | Rationale |
|-----------|-----------------|-----------|
| **UI Local State** | useState, useReducer | Component-internal |
| **Server State** | React Query (TanStack Query) | Caching, refetch, optimistic updates |
| **Global Client State** | Zustand | Concise, minimal boilerplate |
| **Complex Global State** | Zustand + Immer | Immutability convenience |
| **URL State** | nuqs / useSearchParams | Filters, pagination |
| **Form State** | React Hook Form + Zod | Integrated validation |
| **Theme/Language** | Context + Provider | Low change frequency |

### State Placement Decision Flow
```
Should this state be restorable from URL? → URL state
Is it server data? → React Query
Is it shared across multiple components? → Zustand
Is it internal to one component? → useState
Does it have complex transition logic? → useReducer
```

## Next.js App Router Folder Structure

### Recommended Structure (Feature-Based)
```
src/
├── app/                    # Next.js App Router
│   ├── (auth)/             # Auth-related route group
│   │   ├── login/page.tsx
│   │   └── register/page.tsx
│   ├── (main)/             # Main route group
│   │   ├── dashboard/page.tsx
│   │   └── settings/page.tsx
│   ├── api/                # API Routes
│   │   └── [...]/route.ts
│   ├── layout.tsx          # Root layout
│   └── page.tsx            # Home
├── components/
│   ├── ui/                 # General UI (Button, Input, Modal)
│   └── features/           # Feature-specific components
│       ├── auth/
│       └── dashboard/
├── hooks/                  # Custom Hooks
├── lib/                    # Utilities, config
│   ├── api.ts              # API client
│   ├── auth.ts             # Auth utilities
│   └── utils.ts
├── stores/                 # Zustand stores
├── types/                  # TypeScript types
└── styles/                 # Global styles
```

## Component File Conventions

| Item | Rule |
|------|------|
| File Name | PascalCase: `UserProfile.tsx` |
| Directory | kebab-case: `user-profile/` |
| Index | Re-export via `index.ts` |
| Test | `UserProfile.test.tsx` in same directory |
| Story | `UserProfile.stories.tsx` in same directory |
| Types | Same file or separate `types.ts` |

## Performance Optimization Patterns

| Pattern | When | Tool |
|---------|------|------|
| **Memoization** | Expensive computation, frequent re-renders | `useMemo`, `React.memo` |
| **Lazy Loading** | Initial bundle size | `React.lazy`, `next/dynamic` |
| **Virtualization** | 1000+ item lists | `@tanstack/react-virtual` |
| **Image Optimization** | Image loading | `next/image` |
| **Code Splitting** | Per-route splitting | App Router automatic |
| **Optimistic Updates** | Immediate feedback | React Query `onMutate` |
| **Debounce** | Search, input | `useDeferredValue` or custom hook |

## Error Handling Patterns

### Hierarchical Error Boundaries
```
RootErrorBoundary (global)
  └── LayoutErrorBoundary (per section)
      └── ComponentErrorFallback (individual)
```

### API Error Handling
| HTTP Status | Client Handling |
|------------|----------------|
| 401 | Auto logout + redirect |
| 403 | Unauthorized UI |
| 404 | Not Found page |
| 422 | Per-field form error display |
| 429 | Retry + wait notice |
| 500 | Generic error UI + retry button |

## Accessibility (a11y) Checklist

- [ ] Alt text on all images
- [ ] Keyboard navigation (Tab, Enter, Escape)
- [ ] ARIA labels (aria-label, role)
- [ ] Color contrast 4.5:1 or above
- [ ] Visible focus indicator
- [ ] Screen reader testing
- [ ] Semantic HTML (button, nav, main, section)
