---
description: Pre-implementation TanStack docs lookup. Run before coding any TanStack Start/Router/Query task. Extracts relevant topics from the current session plan and fetches official docs to prevent hallucinated patterns.
allowed-tools: Bash(npx @tanstack/cli:*)
---

# Check TanStack Docs

You are about to implement a task involving TanStack. Before writing any code, you must ground yourself in the official documentation.

## Step 1: Identify Topics from Session Context

Review the current session conversation — especially any plan, task description, or feature request discussed so far.

If the context is empty do not extract anything from tanstack docs, inform me that you need context before running the command

Extract every TanStack-relevant concept. Examples of relevant concepts include (but are not limited to):

- Routing (file-based routes, route trees, dynamic routes, pathless routes, layout routes)
- Data loading (loaders, `beforeLoad`, `loader` function, route context)
- Server functions (`createServerFn`, server-only code, RPC)
- Search params (validation, serialization, type inheritance)
- Middleware (request middleware, function middleware, chaining)
- Authentication (sessions, route protection, redirects)
- SSR (hydration, streaming, `DehydrateRouter`, server-side rendering)
- Navigation (`Link`, `useNavigate`, active states, preloading)
- Code splitting (lazy routes, critical path optimization)
- TanStack Query integration (`ensureQueryData`, `useSuspenseQuery`, hydration/dehydration, `QueryClient` in route context)
- Mutations (optimistic updates, invalidation, error handling)
- Caching (`staleTime`, `gcTime`, query keys)
- Error handling (error boundaries, `NotFoundError`, `redirect`, server errors)
- API routes (`createFileRoute` with `server.handlers`)
- Deployment / config (Vite plugin, `app.config.ts`, environment variables)

List all identified topics before proceeding.

## Step 2: Fetch Documentation

For **each** identified topic, run searches across all three relevant libraries. Do not skip libraries — patterns often span multiple packages.

```bash
npx @tanstack/cli search-docs "<topic>" --library start --json
npx @tanstack/cli search-docs "<topic>" --library router --json
npx @tanstack/cli search-docs "<topic>" --library query --json
```

If a search returns a relevant doc page path, fetch its full content:

```bash
npx @tanstack/cli doc <library> <path> --json
```

Run as many searches as needed. Accuracy and depth matter more than speed.

## Step 3: Synthesize a Reference Brief

After all searches complete, produce a **TanStack Reference Brief** with:

1. **Relevant APIs** — the correct function signatures, imports, and usage patterns for this task
2. **Critical gotchas** — anything that behaves differently than expected (especially vs Next.js patterns)
3. **Key constraints** — things the docs explicitly warn against or mark as deprecated

## Step 4: Implementation Ground Rules

- **Only use patterns you found in the docs.** If a pattern, API, or convention did not appear in the search results or fetched doc pages, do not use it. When in doubt, search again.
- **Flag uncertainty.** If the docs are ambiguous or silent on something the task requires, say so explicitly rather than guessing.
- **Note any gotchas discovered.** If the docs mention caveats, deprecations, breaking changes, or "do not do X" warnings, include them in the Reference Brief.
- **No pattern borrowing from other frameworks.** Do not apply conventions from Next.js, Remix, SvelteKit, Nuxt, or any other framework unless the TanStack docs explicitly reference them.

## Output

Present the Reference Brief, then confirm you are ready to begin implementation using only verified TanStack patterns.
