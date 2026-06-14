🧠 The Philosophy & Vision of GoStack
The Problem GoStack Solves
Modern web development in Go is fragmented by design. A typical Go web project looks like:

A router from one library (gorilla/mux, chi, gin)
An ORM from another (gorm, sqlx, ent)
A migration tool from a third (golang-migrate, goose)
A frontend built entirely separately (React, Vue, Svelte) in a different language
A build pipeline stitching them together (Vite, Webpack, Docker Compose)
The result: five ecosystems, five mental models, five failure points — just to build one application.

The GoStack Answer: One Language. One Binary. One Mental Model.
"The complete end-to-end solution for building web applications in Go. It handles the server, the database, the frontend, and the glue that connects them — all within the Go ecosystem."

GoStack is philosophically the Laravel of Go. The rationale borrows directly from what made Laravel dominant in PHP: instead of assembling an app from 10 independent packages, you get one coherent framework where every layer knows about every other layer by design.

The Five Core Pillars
1. 🔋 Batteries Included, Not Bundled GoStack ships with routing, middleware, migrations, query building, view rendering, client reactivity, and a CLI — all in one module. You don't choose your stack. The stack is chosen for you, and everything integrates natively.

2. 🔒 Compile-Time Over Runtime Every decision in GoStack favors catching errors at compile time rather than at runtime:

Schemas are Go code (not YAML or SQL files) — caught by the compiler
Components are compiled ahead-of-time into gostack_components_gen.go — no disk I/O in production
The CLI runs inside the project's own module context — so migrations are always version-aligned
The driver registry uses typed DriverFunc constructors — not interface{} config maps
3. 🏗️ Inversion of Control Without Reflection The DI Container uses a factory registration approach — no struct tags, no reflect.Type scanning. This keeps dependency resolution fast and keeps the compiler's type checker in control. The two-phase boot (Register → Boot) prevents the most common DI bug: resolving a service before it's been registered.

4. 🌐 Go-Native Fullstack (No Separate Frontend) The most radical part of GoStack: the frontend is Go. Components are .html/.css/.js files that get compiled into Go string literals at build time. Client-side reactivity is provided by the gs-* directive system (a micro Alpine.js embedded in the binary). The result is a fullstack app with no Node.js, no npm, no package.json — just go build.

5. 🧩 Modular Self-Containment Each framework package is strictly ordered and independently testable. The contract/ interfaces (Database, Tx) mean you can swap MySQL for Postgres via an environment variable, with zero code changes. The driver registry ensures drivers are never compiled in unless explicitly imported.

The Core Rationale in One Sentence
GoStack exists because Go is an exceptional language held back by ecosystem fragmentation — and the cure is a single, opinionated, compile-safe framework that lets you build the server, the database layer, and the UI without ever leaving Go.

It's positioned as the answer to: "Why would I use Laravel/Rails/Django if I want Go's performance?" The answer GoStack gives is: "You wouldn't have to choose anymore."
