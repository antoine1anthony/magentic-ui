# AGENTS.md

This AGENTS.md file provides AI agents with guidance on how to interact with and contribute to the **magentic-ui** repository, ensuring consistency, code quality, and alignment with project conventions.

## Scope & Precedence

- **Purpose:** Human-authored instructions that AI agents must parse before generating or modifying code in this repo.
- **Scope:** Applies to the entire repository. If nested AGENTS.md files existed (none in this repo), deeper files would override parent instructions.
- **Priority Order:** 1) Direct developer prompts  2) AGENTS.md rules

## Project Structure

```
/  
├─ src/               # React components and entry points
│   ├─ components/    # Reusable UI components (one folder per component)
│   ├─ styles/        # Tailwind config and shared styles
│   └─ index.ts       # Main export surface
├─ stories/           # Storybook stories for visual testing
├─ tests/             # Unit and integration tests (Jest + React Testing Library)
├─ public/            # Static assets
├─ .storybook/        # Storybook configuration
├─ package.json       # Scripts, dependencies, metadata
├─ tsconfig.json      # TypeScript configuration
├─ tailwind.config.js # Tailwind CSS setup
├─ jest.config.js     # Jest setup
├─ .eslintrc.js       # ESLint rules
├─ .prettierrc        # Prettier formatting rules
└─ README.md          # Project overview and instructions
```

## Language & Framework Conventions

### TypeScript & JavaScript

- **Formatting:** Use **Prettier** (no custom overrides) to format code on save; line length 80–100.
- **Linting:** Use **ESLint** with `plugin:@typescript-eslint/recommended` and `eslint-config-prettier` to catch errors and style issues.
- **Imports:** Organize imports alphabetically; group third‑party, local, and style imports with blank lines.

### React & Tailwind

- **Components:** Function components only; name files `PascalCase.tsx`; one default export per file.
- **Styling:** Use **Tailwind CSS** utility classes exclusively; reference shared tokens from `styles/` when possible.
- **Design System:** Leverage **shadcn/ui** for core elements (e.g., `Button`, `Card`) and extend them via composition.
- **Stories:** Each component must have a `.stories.tsx` file under `stories/` demonstrating primary variants.

## Testing & Quality Checks

- **Unit Tests:** Use **Jest** + **React Testing Library**; place tests alongside components in `tests/`
  - Run: `npm test -- --watchAll=false`
- **Type-Check:** `npm run type-check` should pass with zero errors.
- **Lint & Format Check:** `npm run lint` and `npm run format:check` must pass before merging.
- **Storybook:** Validate UI in isolation via `npm run storybook`.

## Build & Distribution

- **Library Build:** `npm run build:lib` produces ESM + CJS bundles in `dist/` with accompanying type declarations.
- **Packaging:** Ensure `package.json` `files` field includes `dist/`, `README.md`, and type definitions.
- **Versioning:** Follow semantic versioning; bump patch for bugfixes, minor for new components, major for breaking changes.

## Docker & CI (if applicable)

- This repo does not include Docker configurations. For CI, ensure GitHub Actions workflow runs:
  1. `npm ci`
  2. `npm run lint`
  3. `npm run format:check`
  4. `npm run type-check`
  5. `npm run test`
  6. `npm run build:lib`

## Agent Behavior Guidelines

- **Initial Read:** Agents **must** read this file before making any changes.
- **Minimality:** Make the smallest change needed to satisfy the prompt, respecting DRY and existing patterns.
- **Validation:** Run lint, format, type-check, test, and build commands locally; ensure all pass before output.
- **Clarification:** If unsure about intent, insert an inline comment or prompt back for developer guidance rather than guessing.
- **Commit Style:** Use conventional commits (e.g., `feat:`, `fix:`, `chore:`) and reference issue/PR when relevant.

*End of AGENTS.md for magentic-ui.*

