---
title: Project Structure
parent: Getting Started
layout: default
nav_order: 5
---

# Project Structure

This is the directory layout of a GoStack project:

```
myapp/
├── cmd/
│   ├── app/
│   │   ├── main.go
│   │   └── gostack_components_gen.go
│   └── gostack/
│       └── main.go
├── internal/
│   ├── controller/
│   ├── model/
│   ├── request/
│   └── middleware/
├── templates/
│   └── components/
├── database/
│   └── migrations/
├── framework/
├── .env
├── go.mod
└── go.sum
```

---

## What each folder is for

`cmd/app/` — The application entrypoint. This is where your server starts.

`cmd/gostack/` — The CLI entrypoint. This is where your command-line tools run.

`internal/controller/` — Your request handlers. Each controller handles a group of related routes.

`internal/model/` — Your database structs. Each model represents a table in your database.

`internal/request/` — Your validation structs. Each request defines rules for incoming data.

`internal/middleware/` — Your request interceptors. Middleware runs before or after your controllers.

`templates/components/` — Your UI components. Each component has HTML, CSS, and JS files.

`database/migrations/` — Your schema change files. Each migration changes your database structure.

`framework/` — The GoStack framework source code. You do not need to modify this.

`.env` — Your environment configuration. This file contains your database credentials and other settings.

`go.mod` — Your Go module definition. This lists your dependencies.

`go.sum` — Your dependency checksums. This ensures consistent builds.

