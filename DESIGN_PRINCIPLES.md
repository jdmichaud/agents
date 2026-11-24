# Design principles

When designing a solution, keep in mind good design practice:

## Structure: how to split the code

- Separation of concerns (Dijkstra, 1974): split the program into parts that
  each deal with a single concern, so that each part can be understood and
  changed without having to think about the others.
- Information hiding (Parnas, 1972): each module hides a design decision that
  is likely to change. This is arguably the most important principle of all,
  and the source of encapsulation.
- High cohesion, low coupling (Constantine): things that change together
  belong together, and things that change independently should depend on each
  other as little as possible.
- Single Responsibility Principle: a module should have one reason to change.
  Put another way, it answers to one stakeholder.
- Deep modules (Ousterhout): a simple interface that hides a lot of
  functionality. The opposite, shallow modules, add interfaces without
  removing any complexity.

## SOLID (Robert C. Martin's acronym)

- S: Single Responsibility (above).
- O: Open/Closed (Meyer): open for extension, closed for modification. You add
  behaviour without editing code that already works.
- L: Liskov Substitution (Liskov, 1987): a subtype must be usable anywhere its
  parent type is, without surprises.
- I: Interface Segregation: many small, client-specific interfaces rather than
  one big one.
- D: Dependency Inversion: business logic depends on abstractions, not on
  details like the database or the framework.
  
## Dependencies between objects
  
- Law of Demeter (Holland, 1987): a method should only talk to its immediate
  collaborators (its own object, its parameters, and the objects it creates or
  holds), not to the objects they return. In short: don't talk to strangers.
- Tell, Don't Ask, a close cousin of Demeter: tell an object to do something
  instead of pulling out its data and deciding for it.
- Composition over inheritance (Gang of Four).
- Program to an interface, not an implementation (Gang of Four).
- Acyclic dependencies: no cycles between modules or packages.
 
## Simplicity

- KISS: keep it simple.
- YAGNI: don't build things "just in case" (from Extreme Programming).
- DRY (Hunt & Thomas): each piece of knowledge should live in one place. It's
  about knowledge, not identical-looking code. Balance it with the Rule of
  Three, and with Sandi Metz's warning: "duplication is far cheaper than the
  wrong abstraction."
- Least astonishment: code should do what its name suggests.
- Kent Beck's four rules of simple design, in priority order:
	a. Passes the tests.
	b. Reveals intention.
	c. No duplication.
	d. Fewest elements.
   
## Correctness

- Make illegal states unrepresentable (Minsky): use types so that invalid data
  can't even be built.
- Parse, don't validate (Alexis King): turn raw input into well-typed values
  once, at the boundary.
- Design by Contract (Meyer): preconditions, postconditions and invariants.
- Command–Query Separation (Meyer): a method either changes state or returns a
  value, not both.
- Fail fast: detect and report errors as early as possible.
- Immutability, and functional core, imperative shell (Gary Bernhardt): pure
  logic in the middle, side effects at the edges.
- Least privilege: give each component only the access it needs.

## Things to keep in mind

- Those principles are in conflict. DRY can create coupling. Strict Demeter can
  multiply wrapper methods. Open/Closed can lead to speculative abstraction,
  which violates YAGNI.
- They are heuristics, not laws. They all serve one goal: keeping the cost of
  change low. When two principles clash, use you judgement and keep the long
  term goal in focus: readability and maintainability.
- You can escape from these principles for one reason: performance. In that
  case, isolate the offending code so that it does not impact overall design.
