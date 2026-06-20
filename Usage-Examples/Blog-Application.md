---
title: Blog Application
parent: Usage Examples
layout: default
nav_order: 1
---

# Blog Application

This example builds a complete blog with posts, comments, and user authentication.

---

## What this example covers

- User registration and login (Guard)
- Creating, editing, and deleting posts (Crafter)
- Commenting on posts (Crafter relationships)
- Admin panel for managing content (GoDash)
- Rendering posts and comments (Tempose)
- Client-side interactivity (Glide)

---

## Models

```go
type User struct {
    ID        int64     `db:"id"`
    Name      string    `db:"name"`
    Email     string    `db:"email"`
    Password  string    `db:"password"`
    CreatedAt time.Time `db:"created_at"`
    UpdatedAt time.Time `db:"updated_at"`
    Posts     []Post    `rel:"has_many" fk:"user_id" table:"posts"`
    Comments  []Comment `rel:"has_many" fk:"user_id" table:"comments"`
}

type Post struct {
    ID        int64     `db:"id"`
    UserID    int64     `db:"user_id"`
    Title     string    `db:"title"`
    Body      string    `db:"body"`
    CreatedAt time.Time `db:"created_at"`
    UpdatedAt time.Time `db:"updated_at"`
    User      *User     `rel:"belongs_to" fk:"user_id" table:"users"`
    Comments  []Comment `rel:"has_many" fk:"post_id" table:"comments"`
}

type Comment struct {
    ID        int64     `db:"id"`
    PostID    int64     `db:"post_id"`
    UserID    int64     `db:"user_id"`
    Body      string    `db:"body"`
    CreatedAt time.Time `db:"created_at"`
    UpdatedAt time.Time `db:"updated_at"`
    User      *User     `rel:"belongs_to" fk:"user_id" table:"users"`
    Post      *Post     `rel:"belongs_to" fk:"post_id" table:"posts"`
}
```

---

## Routes

```go
router.Get("/", homeHandler)
router.Get("/posts/:id", showPostHandler)

router.Group("/posts", []http.Middleware{AuthMiddleware}, func(g *http.RouteGroup) {
    g.Get("/create", createPostFormHandler)
    g.Post("/create", createPostHandler)
    g.Get("/:id/edit", editPostFormHandler)
    g.Post("/:id/edit", updatePostHandler)
    g.Post("/:id/delete", deletePostHandler)
})

router.Group("/comments", []http.Middleware{AuthMiddleware}, func(g *http.RouteGroup) {
    g.Post("/create", createCommentHandler)
})

router.Get("/login", loginFormHandler)
router.Post("/login", loginHandler)
router.Get("/register", registerFormHandler)
router.Post("/register", registerHandler)
router.Post("/logout", logoutHandler)
```

---

## Controllers

**PostController**

```go
func (c *PostController) Index(ctx *http.Context) {
    var posts []model.Post
    err := gostack.Table("posts").
        OrderBy("created_at", "DESC").
        With("User", "Comments").
        Get(&posts)
    if err != nil {
        return ctx.JSON(500, map[string]string{"error": "Failed to fetch posts"})
    }
    ctx.Render("posts/index", map[string]any{"posts": posts})
}

func (c *PostController) Show(ctx *http.Context) {
    id := ctx.Query("id")
    var post model.Post
    err := gostack.Table("posts").
        Where("id", "=", id).
        With("User", "Comments.User").
        First(&post)
    if err != nil {
        return ctx.Render("posts/404", nil)
    }
    ctx.Render("posts/show", map[string]any{"post": post})
}

func (c *PostController) Create(ctx *http.Context) {
    user := ctx.Get("user").(*model.User)
    title := ctx.Post("title")
    body := ctx.Post("body")
    
    _, err := database.Create[model.Post](c.db, map[string]any{
        "user_id": user.ID,
        "title":   title,
        "body":    body,
    })
    if err != nil {
        return ctx.Render("posts/create", map[string]string{"error": "Failed to create post"})
    }
    ctx.Writer.Header().Set("Location", "/")
    ctx.Writer.WriteHeader(302)
}
```

**CommentController**

```go
func (c *CommentController) Create(ctx *http.Context) {
    user := ctx.Get("user").(*model.User)
    postID := ctx.Post("post_id")
    body := ctx.Post("body")
    
    _, err := database.Create[model.Comment](c.db, map[string]any{
        "post_id": postID,
        "user_id": user.ID,
        "body":    body,
    })
    if err != nil {
        ctx.Writer.Write([]byte("Failed to post comment"))
        return
    }
    ctx.Writer.Header().Set("Location", "/posts/"+postID)
    ctx.Writer.WriteHeader(302)
}
```

---

## Views

**posts/index.html** — Lists all posts

```html
<div gs-css>
    <h1>Blog</h1>
    {{ range .posts }}
    <article>
        <h2><a href="/posts/{{ .ID }}">{{ .Title }}</a></h2>
        <p>By {{ .User.Name }} on {{ .CreatedAt.Format "Jan 02, 2006" }}</p>
        <p>{{ .Body }}</p>
        <p>{{ len .Comments }} comments</p>
    </article>
    {{ end }}
    <a href="/posts/create">New Post</a>
</div>
```

**posts/show.html** — Single post with comments

```html
<div gs-css>
    <h1>{{ .post.Title }}</h1>
    <p>By {{ .post.User.Name }} on {{ .post.CreatedAt.Format "Jan 02, 2006" }}</p>
    <p>{{ .post.Body }}</p>
    
    <h3>Comments</h3>
    {{ range .post.Comments }}
    <div>
        <strong>{{ .User.Name }}</strong>
        <p>{{ .Body }}</p>
    </div>
    {{ end }}
    
    <form action="/comments/create" method="POST">
        <input type="hidden" name="post_id" value="{{ .post.ID }}">
        <textarea name="body" placeholder="Add a comment..."></textarea>
        <button type="submit">Post Comment</button>
    </form>
</div>
```

---

## Admin Panel

Register models to get an admin interface:

```go
admin.Register(&model.User{})
admin.Register(&model.Post{})
admin.Register(&model.Comment{})
```

This creates a `/admin` panel where you can create, edit, and delete posts, users, and comments without writing any additional code.

---

## Authentication

All post creation, editing, and deletion routes use `AuthMiddleware` to ensure only logged-in users can modify content.

Comments also require authentication.

```go
router.Get("/posts/create", createPostFormHandler, auth.RequireAuth(gostack.Auth, "session"))
```

---

## Next Steps

This blog is functional but can be extended with:

- Post tags and categories
- User profiles
- Search functionality
- Email notifications for new comments
- RSS feed

The same patterns apply to all these extensions.
```
