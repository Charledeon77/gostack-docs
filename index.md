---
title: Home
layout: home
---

<!-- Logo -->
<p align="center">
  <img src="https://raw.githubusercontent.com/Charledeon77/gostack-docs/main/assets/images/gostack-2d-logo-rectangular.jpg" alt="GoStack Logo" style="width:100%">
</p>

<!-- Badges -->
<p align="center">
  <img src="https://img.shields.io/badge/CI-passing-brightgreen"/>
  <img src="https://img.shields.io/badge/codecov-81%25-yellow"/>
  <img src="https://img.shields.io/badge/Go-1.26-blue"/>
  <img src="https://img.shields.io/badge/Echo-v4-lightgrey"/>
  <img src="https://img.shields.io/badge/SolidJS-1.8-blueviolet"/>
  <img src="https://img.shields.io/badge/Tailwind_CSS-4.3-09f"/>
  <img src="https://img.shields.io/badge/PostgreSQL-16-blue"/>
  <img src="https://img.shields.io/badge/License-MIT-green"/>
</p>

<p align="center">
  <b>GoStack</b> — <i>A modern fullstack web framework for scalable web development in Go.</i>
</p>

# 📝 The Philosophy & Vision of GoStack  
## The Problem GoStack Solves  

Modern **Web development** in **Go** is fragmented by design. A typical Go Web project looks like:

1. ) **Router** from a third-party library (*<code>gorilla/mux</code>*)

2. ) **ORM** from a third-party library (*<code>gorm</code>*)

3. ) **Migration** tool from a third-party library (*<code>golang-migrate</code>*)

4. ) **Authentication** system from a third-party library (*<code>goth</code>*)

5. ) **Caching** layer from a third-party library (*<code>go-redis</code>*)

6. ) **Queue**/background worker from a third-party library (*<code>machinery</code>*)

7. ) **WebSocket** library from a third-party library (*<code>gorilla/websocket</code>*)

8. ) **Cron** scheduler from a third-party library (*<code>robfig/cron</code>*)

9. ) **File storage** abstraction from a third-party library (*<code>aws-sdk-go</code>*)

10. ) **Frontend** built entirely separately (*<code>React</code>*) in a different language, introducing context-switching, with its own third-party ecosystem (*<code>Vite</code>*)

**The result**: Ten third-party ecosystems, Ten mental models, Ten failure points — just to build one application.

**The GoStack Answer**: One Language. One Binary. One Mental Model.

#
# The Disruptive Paradigm Shift: GOSTACK

**GoStack** is the first complete end-to-end framework solution for building **FullStack Web applications** in Go. It handles the:

1. ) ✅ **Server** *(Citadel)* — IoC service container and unified bootstrapping kernel
2. ) ✅ **Middleware** *(Navigator)* — pipeline-aware routing engine with onion-style middleware
3. ) ✅ **ORM** *(Crafter)* — compile-time safe Active Record ORM with model hooks and hydration
4. ) ✅ **Schema Builder** *(Grapher)* — declarative fluent schema builder for database definitions
5. ) ✅ **Migrations** *(Traveller)* — auto-schema diffing migration runner with transaction support
6. ) ✅ **Authentication** *(Guard)* — session/token auth with CSRF and policy-based RBAC
7. ) ✅ **Caching** *(Mory)* — strongly-typed generic caching adapter
8. ) ✅ **Queue** *(Sequence)* — background worker with retries, delays, job chains, and batches
9. ) ✅ **Events** *(Spark)* — sync and async Pub/Sub event dispatcher
10. ) ✅ **Mail** *(GoMail)* — rich SMTP HTML mailer built on the standard library
11. ) ✅ **Storage** *(Vault)* — traversal-secure local and S3 storage sandbox
12. ) ✅ **Scheduler** *(Planner)* — native cron-style task scheduler running in background
13. ) ✅ **Admin Dashboard** *(GoDash)* — auto-generated admin panel with live queue monitoring
14. ) ✅ **Frontend Compiler** *(Tempose)* — AOT compiler turning HTML/CSS/JS into Go code
15. ) ✅ **Client Reactivity** *(Glide)* — zero-dependency reactive directive engine
16. ) ✅ **CLI** *(Gost)* — interactive scaffolding for migrations, models, and controllers
17. ) ✅ **Config** *(GoCon)* — environment-based configuration management.
18. ) ✅ **Everything** else in-between, and the glue that connects them — all within the **Go** ecosystem.

Everything in **One binary, One mental model, One language**.   

It's the equivalent of what **Laravel** gave **PHP**, what **Django** gave **Python**, and what **Rails** gave **Ruby** — instead of assembling an app from 10 independent packages, you get one coherent framework where every layer knows about every other layer by design.

**Go** developers have never had this — until now (June 2026).

# The Five (5) Core Pillars
## 1.) 🔋 Batteries Included:

**GoStack** ships with everything — routing, ORM, migrations, auth, caching, queues, WebSockets, scheduling, storage, events, admin dashboard, and a frontend compiler — all in one module, which means no abandonware risk, no integration hell, no context switching between Go and Node.js, no tracking ten different package versions, and no JavaScript frontend forced upon you, because everything is natively integrated, maintained as one coherent ecosystem, and compiled into a single binary, so you don't assemble a stack — you just build.

#
## 2.) 🔄 No Context Switching (Go-Native Fullstack)

The most radical part of GoStack: the frontend is Go. Components are `.html`, `.css`, and `.js` files that **Tempose** compiles into Go string literals at build time — no separate dev server, no proxy configuration, no CORS headaches.

**Client-side reactivity** is provided by **Glide**, a micro frontend engine inspired by Alpine.js, embedded directly in your binary. With Glide's `gs-*` directive system, you add interactivity using declarative attributes right in your HTML — `gs-click`, `gs-model`, `gs-show`, `gs-for`, and more. No `useState`, no `useEffect`, no virtual DOM, no build step. Just HTML with superpowers.

The result is a fullstack application with no Node.js, no `npm`, no `package.json`, no `node_modules`, no Webpack, no Vite, no Babel — just `go build`.   

**One language. One binary. No separate frontend toolchain**.

#
## 3.) 📘 Easy to Learn and Use (One Mental Model)

When you learn a new framework, you're not just learning syntax — you're learning a way of thinking. Most frameworks teach you ten different ways of thinking: one for data, one for background tasks, one for real-time updates, one for configuration. Every new feature demands a new mental context switch.

GoStack doesn't do this — everything in GoStack works the way you'd naturally expect it to work. The pattern you learn on day one is the same pattern you use every time forward. There are no hidden layers where the framework suddenly behaves differently because you've crossed some invisible complexity threshold.

With GoStack, there's just one simple pattern that never changes, no matter how big your idea gets.

#
## 4.) 🔒 Secure by Default

Most frameworks assume you'll remember to lock the door after you build the house. GoStack assumes you won't — so it locks every door for you, before you even lay the first brick.

With GoStack, security isn't an afterthought you scramble to add at the end of a project. It's baked into the foundation from the very first line. Every request is questioned. Every file access is contained. Every database query is protected unless you explicitly say otherwise. Every user action needs permission. Nothing is trusted by accident.

This means you can build with speed and sleep with peace of mind. Beginners don't have to become security experts just to launch their first app. Investors don't have to worry about the hidden cost of a breach. And developers don't have to spend their nights wondering if they forgot to sanitize that one input.

GoStack doesn't wait for you to make a mistake — it prevents the mistake from ever happening. Security isn't a feature you add later. It's how the framework works, baked in and always on.

## 5. ⚡ Developer Experience as a First-Class Feature

For years, developers in other ecosystems have enjoyed something Go never had: a complete, integrated framework where every piece works with every other piece out of the box. Rails has it. Django has it. Laravel has it.

Go developers have built amazing things too — but not because of the tooling. Despite it. Go developers have built amazing things too — but not because of the tooling. Despite it. Go developers have always had to build integration themselves, piece by piece, and then maintain it forever. A router here. An ORM there. A queue library over here. A WebSocket package somewhere else. Ten different ecosystems. Ten different futures. Ten chances for any one of them to fall out of sync with your needs.

GoStack delivers what Go has always deserved: a complete, integrated framework designed from the ground up to be **Future-Proof by Default**. No hunting for which router works with which ORM. No wondering if your WebSocket library will still be maintained next year. No constant context switching between packages with different philosophies.

The result is simple: one stack, one way of working, one future. No assembly required. No fragmentation. No guesswork.

Other ecosystems have enjoyed this foundation for years. GoStack brings it to the Go ecosystem, to finally remove those headaches and uncertainties.

GoStack handles the heavy lifting and the behind-the-scenes complexity. While you handle your ambition and concentrate on your core business objectives.

# The Core Rationale in One Sentence
GoStack exists because Go is an exceptional language held back by ecosystem fragmentation — and the cure is a single, opinionated, compile-safe framework that lets you build the server, the database layer, and the UI without ever leaving Go.

It's positioned as the answer to: "Why would I use Laravel/Rails/Django if I want Go's performance?" The answer GoStack gives is: "You wouldn't have to choose anymore."
