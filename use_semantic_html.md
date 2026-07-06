## Use Semantic HTML

---

_Semantics_ simply means "the meaning of something". Semantic html tags are tags that give meaning to the content on the page. E.g.:, `<h1>`  is semantic html. It tells the browser that this is "the top level heading". 

Use semantic html wherever possible. With CSS you could make any text look like a `h1`, but it would have no semantic value. Semantic html is understood by browsers, which ensures your content is rendered properly. It also benefits search engines and screen readers. 

There are about a hundred or so semantic HTML tags, but these are the essential ones to know:
`<article>` `<aside>` `<details>` `<figure>` `<figcaption>` `<footer>` `<form>` `<header>` `<main>` `<mark>` `<nav>` `<section>` `<summary>` `<time>`

These tags have meaning behind them that are understood by browsers, search engines, screen readers, etc. 

> [!TIP]
> Start with semantic tags. If you encounter a situation where no semantic tags are appropriate, then use non-semantic tags like `<div>`.

### How to arrange semantic tags: 

After the closing </head> tag, inside <body>:

* The page typically opens with <header>, which holds your <h1>, logo, and <nav>.
* Every page should have exactly one <main>. This is where the core content lives.
* <section> and <article> belong inside <main>.
* <footer> sits outside <main>, at the bottom of the page.

Think of it as a document with a clear hierarchy: a header to orient the reader, a main body to deliver the content, and a footer to close it out.



