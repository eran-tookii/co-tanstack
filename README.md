# co-tanstack

Custom [Claude Code](https://docs.anthropic.com/en/docs/claude-code) commands for TanStack development. Grounds your AI-assisted coding in official TanStack documentation so you get correct patterns instead of hallucinated ones.

## What it does

Before you implement anything with TanStack Start, Router, or Query, the `co-tanstack` command:

1. **Scans your session context** — extracts every TanStack-relevant concept from your current plan or task
2. **Fetches official docs** — searches across Start, Router, and Query using `@tanstack/cli`
3. **Produces a Reference Brief** — correct API signatures, gotchas, and constraints
4. **Enforces doc-only patterns** — no guessing, no borrowing from Next.js/Remix/etc.

## Installation

Copy the command into your project's Claude Code commands directory:

```bash
# From your project root
mkdir -p .claude/commands
cp co-tan/commands/co-tanstack.md .claude/commands/
```

Or clone and symlink:

```bash
git clone https://github.com/eran-tookii/co-tan.git
ln -s "$(pwd)/co-tan/commands/co-tanstack.md" .claude/commands/co-tanstack.md
```

## Prerequisites

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) CLI
- [`@tanstack/cli`](https://www.npmjs.com/package/@tanstack/cli) (invoked via `npx`, no global install required)

## Usage

In a Claude Code session, when you're about to work on a TanStack feature:

```
/co-tanstack
```

The command needs session context to work — have a plan or task description in your conversation first. If the context is empty, it will ask you to provide one before proceeding.

## Covered Topics

The command recognizes and looks up docs for:

- Routing (file-based, dynamic, pathless, layout routes)
- Data loading (loaders, `beforeLoad`, route context)
- Server functions (`createServerFn`, RPC)
- Search params (validation, serialization, type inheritance)
- Middleware (request, function, chaining)
- Authentication (sessions, route protection, redirects)
- SSR (hydration, streaming, `DehydrateRouter`)
- Navigation (`Link`, `useNavigate`, active states, preloading)
- Code splitting (lazy routes, critical path optimization)
- TanStack Query integration (`ensureQueryData`, `useSuspenseQuery`)
- Mutations (optimistic updates, invalidation)
- Caching (`staleTime`, `gcTime`, query keys)
- Error handling (error boundaries, `NotFoundError`, `redirect`)
- API routes (`createFileRoute` with `server.handlers`)
- Deployment / config (Vite plugin, `app.config.ts`)

## Contributing

Contributions are welcome! If you have ideas for new commands or improvements to existing ones, please open an issue or submit a pull request.

## License

[MIT](LICENSE)
