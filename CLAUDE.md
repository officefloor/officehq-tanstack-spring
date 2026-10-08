# Working in this app

Implement the change request you have been given. A single change may span the
database schema, the server, and the front end.

- **`data-testid` is an immutable public API.** Expose a stable `data-testid` on every
  element and value a feature surfaces, and **never rename or remove a `data-testid`
  that already exists** — it is how the app is tested. Match exactly the `data-testid`
  values your task's test expects.
- **Run `bin/e2e`** to build the app, start it, run your test, and stop — use it to
  check your work. The `bin/` scripts and these two instruction files are fixed; do
  not edit them.

---

*TanStack's own documentation is vendored in this repo under `docs/tanstack/`: the official
`llms.txt` index for TanStack Router (`router.llms.txt`) and TanStack Query (`query.llms.txt`).
Consult it when working with TanStack Router or Query.*

---

*Spring's official reference documentation is the guidance for this stack — consult it when
working on the server: Spring Boot <https://docs.spring.io/spring-boot/4.1/reference/> and Spring
Framework (web MVC, the `@RestController` layer) <https://docs.spring.io/spring-framework/reference/>.*
