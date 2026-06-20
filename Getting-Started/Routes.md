---
title: Routes (Navigator)
parent: Getting Started
layout: default
nav_order: 6
---

# Routes (Navigator)

Navigator listens for incoming HTTP requests and directs each one to the correct location.

---

## Creating a route

In your `main.go`, register a route:

```go
router.Get("/hello", func(ctx *http.Context) {
    ctx.Writer.Write([]byte("Hello, World!"))
})
```

## HTTP methods

Navigator supports:

`router.Get()` — for retrieving data

`router.Post()` — for creating data

`router.Put()` — for updating data

`router.Patch()` — for partial updates

`router.Delete()` — for removing data

## Route groups

Group related routes together with a shared prefix:

```go
router.Group("/api", []http.Middleware{}, func(g *http.RouteGroup) {
    g.Get("/users", listUsers)
    g.Post("/users", createUser)
})
```


