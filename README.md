# officehq-tanstack-spring — base repository (additive React SPA + plain Spring Boot)

A **base repository** for the `ui-long-degradation-test` harness — **one technology stack**:
front-end an **additive React SPA** (TanStack Router + TanStack Query + a slot registry), backend
**plain Spring Boot** (`@RestController` + `@Service`) on in-memory H2. No OfficeFloor.

This arm exists to make the front-end result **attributable**. Every other UI arm shares the
additive OfficeFloor backend, so the study cannot yet say whether front-end additivity is
self-sufficient. Against `~/officehq-tanstack-officefloor` **only the backend differs** — the
front end is byte-identical, because this repo was cloned from it:

* if this arm holds its front-end structure too, the front-end result stands **independently**;
* if it degrades, the two layers **interact**, and additivity has to be whole-stack — a more
  interesting finding, and more useful to anyone adopting it.

Either answer is publishable; not knowing is the weak position.

Every shared structure here is **generated from the file system** or **addressed by a key**, so a
feature is new files:

| what is added          | the file that is added                  | what is edited |
| ---------------------- | --------------------------------------- | -------------- |
| a page                 | `routes/<path>.tsx`                     | nothing (the route tree is generated) |
| its nav link           | `features/<f>/nav.slot.tsx`             | nothing (the shell lists no pages) |
| a drill-in / detail    | `routes/<section>.$id.tsx`              | nothing (the router decides, not a flag) |
| a panel/column/action  | `features/<f>/<thing>.slot.tsx`         | nothing (the page lists no contents) |
| a filter / sort/ tab   | `features/<f>/<control>.slot.tsx`       | nothing (its state is a URL key) |
| data for any of them   | a `useQuery` key in that file           | nothing (the cache is a keyspace) |

See `CLAUDE.md` for the five rules the agent works to, and `src/main/frontend/slots/Slot.tsx` for
the contribution mechanism. It is the
near-empty starting point (base shell + Spring/OfficeFloor + empty H2, no tables) that the harness
**evolves** into a full application over ~60 English change requests, one full-stack change per
checkpoint.

- Base repos are **home-level sibling directories**, one per stack, named
  `~/officehq-<frontend>-<backend>` so both layers are visible (`~/officehq-react-officefloor`,
  `~/officehq-<frontend>-<backend>`, …) — the **front-end and the backend may both vary** between
  stacks. The study compares stacks by running the harness against each in turn — which stack best
  resists erosion.
- The harness (`~/ui-long-degradation-test`, `config.yaml → app.repo`) reads this folder at branch
  **`base-empty`**, worktrees it onto `evolve/<run_id>/<condition>/chain<n>`, and commits each
  checkpoint there. This branch is only ever read.
- It honours the **App contract** — see `~/ui-long-degradation-test/docs/SUT_CONTRACT.md`.
- **Try another stack:** create a new sibling `~/officehq-<frontend>-<backend>` (different
  front-end, different backend, or both), satisfy the same `BASE_CHECKLIST.md`, and point
  `app.repo` at it. Each is its own run.

**Status: green.** `bin/build` produces the one jar and `bin/e2e` verified the shell against the
real jar. Confirmed the packaged jar contains **no OfficeFloor libraries**. The front-end shell is
byte-identical to `~/officehq-tanstack-officefloor`.
