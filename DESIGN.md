# Design of this implementation

Stack-specific guidance for this implementation of the app: its stack, layout and conventions.
Read it with `AGENTS.md`, which has the working rules and how the app is tested.

*TanStack's own documentation is vendored in this repo under `docs/tanstack/`: the official
`llms.txt` index for TanStack Router (`router.llms.txt`) and TanStack Query (`query.llms.txt`).
Consult it when working with TanStack Router or Query.*

---

## Spring

This is a standard Spring Boot application, built with conventional Spring MVC
(`@RestController` request handling, a service layer, Spring Data / JPA persistence, and Bean
Validation). Follow ordinary Spring conventions and idioms throughout. Spring's reference
documentation is the guidance for the server: Spring Boot
<https://docs.spring.io/spring-boot/4.1/reference/> and Spring Framework
<https://docs.spring.io/spring-framework/reference/>.
