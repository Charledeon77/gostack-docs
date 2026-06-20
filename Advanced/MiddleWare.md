---
title: Middleware (Bridge)
parent: Advanced
layout: default
nav_order: 2
---

# Middleware (Bridge)

Bridge intercepts incoming HTTP requests before they reach your controller. It can also run code after your controller sends a response.

---

## What it does

Middleware sits between the router and your controller. It can:

- Check if a user is logged in
- Log every request
- Add headers to responses
- Validate input
- Stop a request from reaching the controller if conditions are not met

---

## Signature

A middleware function has this shape:

```go
func MyMiddleware(ctx *http.Context, next http.NextHandler) error {
    // Code here runs before the controller
    
    err := next(ctx)
    
    // Code here runs after the controller
    
    return err
}
```

You call `next(ctx)` to pass control to the next middleware or the controller.

If you return an error without calling `next(ctx)`, the request stops.

---

## Example: Auth Middleware

```go
func AuthMiddleware(ctx *http.Context, next http.NextHandler) error {
    user, ok := gostack.Auth.User(ctx.Request)
    if !ok {
        return ctx.JSON(401, map[string]string{"error": "Unauthorized"})
    }
    ctx.Set("user", user)
    return next(ctx)
}
```

This middleware checks if a user is logged in. If not, it returns a 401 response and stops the request.

If the user is logged in, it stores the user in the context and passes control to the next middleware or controller.

---

## Example: Logger Middleware

```go
func LoggerMiddleware(ctx *http.Context, next http.NextHandler) error {
    start := time.Now()
    
    err := next(ctx)
    
    elapsed := time.Since(start)
    fmt.Printf("%s %s took %s\n", ctx.Request.Method, ctx.Request.URL.Path, elapsed)
    
    return err
}
```

This middleware logs how long each request takes.

---

## Registering middleware

**On a single route:**

```go
router.Get("/dashboard", dashboardHandler, AuthMiddleware, LoggerMiddleware)
```

**On a route group:**

```go
router.Group("/admin", []http.Middleware{AuthMiddleware, LoggerMiddleware}, func(g *http.RouteGroup) {
    g.Get("/users", listUsers)
    g.Post("/users", createUser)
})
```

---

## Built-in middleware

GoStack provides these middleware functions:

`http.Logger` — Logs request method, path, status, and duration.

`http.RequireAuth` — Blocks unauthenticated requests.

`http.Guest` — Redirects authenticated users away from login/register pages.

`http.SessionMiddleware` — Loads and saves session data.

`auth.CSRF` — Validates CSRF tokens on state-changing requests.

`http.ValidateRequest` — Validates JSON request bodies against struct rules.

---

## Order matters

Middleware runs in the order you register it.

```go
router.Get("/path", handler, FirstMiddleware, SecondMiddleware)
```

FirstMiddleware runs first. Then SecondMiddleware. Then the handler.

If FirstMiddleware calls `next(ctx)`, control passes to SecondMiddleware. If FirstMiddleware returns without calling `next(ctx)`, SecondMiddleware and the handler never run.

