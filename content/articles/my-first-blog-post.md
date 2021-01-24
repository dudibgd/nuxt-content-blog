---
title: My first Blog Post
description: NOVI Learning how to use @nuxt/content to create a blog
img: /images/dudi1.jpg
alt: my first blog post
author:
  name: Benjamin
  bio: All about Benjamin
  image: https://images.unsplash.com/photo-1533636721434-0e2d61030955?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2550&q=80
---



## h2 - My first blog post

Welcome to my first blog post using content module



```js[nuxt.config.js]
export default {
  nuxt: "is the best"
}
```
```html[my-first-blog-post.md]
<p>code styling is easy</p>
```


<div class="bg-blue-500 text-white p-4 mb-4">
  This is HTML inside markdown that has a class of note
</div>

## This is a heading

This is some more info

<info-box>
  <template #info-box>
    This is a vue component inside markdown using slots
  </template>
</info-box>

## This is another heading

This is some more info

### This is another sub heading

This is some more info

## This is another heading

This is some more info

<script>

</script>