---
title: Service Container (Citadel)
parent: Advanced
layout: default
nav_order: 1
---

# Service Container (Citadel)

Citadel is GoStack's dependency injection container. It manages how your services are created and shared across your application.

---

## What it does

Citadel holds your service definitions. When you need a service, you ask Citadel for it. Citadel creates it and gives it to you.

---

## Bindings

You register a service with Citadel using one of two methods:

**Singleton** — Citadel creates the service once and returns the same instance every time you ask for it.

```go
container.BindSingleton("db", func(c *foundation.Container) any {
    return database.NewSQLAdapter("mysql", dsn)
})
```

**Transient** — Citadel creates a new instance every time you ask for it.

```go
container.BindTransient("logger", func(c *foundation.Container) any {
    return log.New(os.Stdout, "APP: ", log.LstdFlags)
})
```

---

## Resolving

To get a service from Citadel:

```go
db, err := container.Resolve("db")
```

If the service is not registered, Citadel returns an error.

---

## Service Providers

Service providers organize your registrations into reusable groups.

```go
type DatabaseProvider struct{}

func (p *DatabaseProvider) Register(c *foundation.Container) {
    c.BindSingleton("db", func(c *foundation.Container) any {
        return database.NewSQLAdapter("mysql", dsn)
    })
}

func (p *DatabaseProvider) Boot(c *foundation.Container) {
    db := c.Resolve("db").(contract.Database)
    db.Connect()
}
```

The `Register` phase binds services. The `Boot` phase runs after all services are registered, so you can safely resolve other services.
