---
title: Getting Started
has_children: true
nav_order: 1
---

# What is GoStack?

GoStack is a fullstack web framework for the Go programming language.

It gives you everything you need to build a web application in one system. You do not need to search for a router, an ORM, a migration tool, an authentication system, a caching layer, a queue worker, a WebSocket library, a cron scheduler, or a file storage driver. GoStack provides all of them.

Everything works together because everything is built together.

GoStack handles the server, the database, the background jobs, the scheduled tasks, and the frontend — all in Go. You do not need to leave Go to build a complete web application.

---

## What GoStack includes

**HTTP Layer**
- Router (Navigator) — directs incoming requests to the correct handler
- Middleware (Bridge) — intercepts requests before they reach your handler
- Session management — remembers users between requests
- CSRF protection — prevents cross-site request forgery attacks
- WebSockets — real-time communication between server and browser

**Database**
- ORM (Crafter) — represents database tables as Go structs
- Query Builder — constructs SQL queries using Go methods
- Migrations (Traveller) — changes your database schema using Go code
- Schema Builder (Grapher) — defines database tables using Go code

**Authentication**
- Session-based login (Guard) — cookie-based authentication for web apps
- Token-based login (Guard) — API token authentication for mobile or API clients
- Authorization (Gates and Policies) — controls what each user can do

**Background Processing**
- Queue (Sequence) — runs tasks in the background
- Events (Spark) — publishes and listens for application events
- Scheduler (Planner) — runs tasks at specific times or intervals

**Other Features**
- Cache (Mory) — stores data in memory for fast retrieval
- Email (GoMail) — sends emails via SMTP
- File Storage (Vault) — saves and retrieves files
- Admin Panel (GoDash) — automatically generated CRUD interface
- Social Login (SocialHub) — OAuth2 login with GitHub and Google
- Frontend Compiler (Tempose) — compiles HTML/CSS/JS into Go code
- Client Reactivity (Glide) — interactive HTML without JavaScript frameworks
- CLI (Gost) — command-line tools for generating code and running tasks
- Configuration (GoCon) — reads settings from `.env` files

---

## Who is GoStack for?

GoStack is for Go developers who want to build web applications without assembling a stack from ten different libraries. It is for developers who want one system where everything works together out of the box.

It is also for beginners who are new to Go and want a framework that guides them toward good practices without forcing them to become experts in every subsystem before they can build something useful.

---

## What GoStack is not

GoStack is not a microframework. It is not designed for building tiny APIs with minimal overhead. If you need a small, lightweight HTTP server with no additional features, Go's standard library or a microframework may be a better choice.

GoStack is a fullstack framework. It is designed for building complete web applications with databases, authentication, background jobs, and frontend components.

---

