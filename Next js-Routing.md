# Next.js

# How to install Next.js ??

<aside>
💡

```jsx
npx ****create-next-app@latest
```

</aside>

# Run the development server

<aside>
💡

1. Run `npm run dev` to start the development server.
2. Visit `http://localhost:3000` to view your application.
</aside>

# Routing in Next.js

<aside>
💡

Next.js is Filesystem-based Routing ( uses files and folders to define routes)

!! only files and folders inside “app” folder are considered

Example: create an index page (`/`):

![image.png](image.png)

```jsx
export default function Page() {
  return <h1>Hello Next.js!</h1>
}
```

</aside>

# In Next.js

<aside>
💡

- **Folders** are used to define the route segments that map to URL segments.
- **Files** (like `page` and `layout`) are used to create UI that is shown for a segment.

![image.png](image%201.png)

</aside>

# Dynamic Routes

<aside>
💡

For dynamic paths like `/blog/post-1`, `/blog/post-2`, etc., use **square brackets** syntax:

app/
  blog/
    [slug]/
      page.js -> route: /blog/:slug

This allows you to render **dynamic** content for each blog post without needing a new folder for each one.

![image.png](image%202.png)

![image.png](image%203.png)

</aside>

# Linking between Pages using <Link>

```jsx
import Link from 'next/link'
 
export default async function Post({ post }) {
  const posts = await getPosts()
 
  return (
    <ul>
      {posts.map((post) => (
        <li key={post.slug}>
          <Link href={`/blog/${post.slug}`}>{post.title}</Link>
        </li>
      ))}
    </ul>
  )
}
```

# Reserved File Names

<aside>
💡

Important: These filenames are only reserved when creating them inside of the `app/` folder (or any subfolder). Outside of the `app/` folder, these filenames are not treated in any special way.

Here's a list of reserved filenames in Next JS - you'll, of course, learn about the important ones throughout this section:

- `page.js` => Create a new page (e.g., `app/about/page.js` creates a `<your-domain>/about` page)
- `layout.js` => Create a new layout that wraps sibling and nested pages
- `not-found.js` => Fallback page for "Not Found" errors (thrown by sibling or nested pages or layouts)
- `error.js` => Fallback page for other errors (thrown by sibling pages or nested pages or layouts)
- `loading.js` => Fallback page which is shown whilst sibling or nested pages (or layouts) are fetching data
- `route.js` => Allows you to create an API route (i.e., a page which does NOT return JSX code but instead data, e.g., in the JSON format)
</aside>