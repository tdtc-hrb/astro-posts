---
layout: ../../layouts/MarkdownPostLayout.astro
title: "布局 - html"
description: "Scalable Vector Graphics"
date: 2026-10-14
author: "tdtc"
---
![](https://developer.mozilla.org/shared-assets/images/diagrams/learn/structuring-documents/site-structure.svg)

- header
> top
- main
> middle
- footer
> bottom

### example
> The code below is within the body element.
```
    <header>
        <section>
          <h1>Action Link</h1>
        </section>
        <nav>
          <ul>
            <li><a href="#">Home</a></li>
            <li><a href="#">Contact</a></li>
          </ul>
        </nav>
    </header>

    <!-- Our page's main content -->
    <main>
      <div>
          <h3>Difference between div, section, and article in HTML</h3>

          <p>
            Some screen readers will announce an article and allow the user to navigate by article.
          </p>

      </div>

      <article>
        <h2>Using HTML5 section element</h2>

        <section>
            <p>
               However, the div is a semantically neutral element, whereas the section element is not. 
               The section element is exposed through the browser's accessibility Application Programming Interface (API).
            </p>
        </section>

      </article>

      <!-- the aside content can also be nested within the main content -->
      <aside>
        <h2>Related</h2>

        <ul>
          <li><a href="https://forum.freecodecamp.org/t/difference-between-div-section-and-article-in-html/597786">bbsmooth</a></li>
          <li><a href="https://www.w3.org/WAI/GL/wiki/Using_HTML5_section_element">WCAG Working Group</a></li>
        </ul>
      </aside>
    </main>

    <footer>
      <p>©Copyright 2050 by nobody. All rights reversed.</p>
    </footer>
```

## Ref
- [Structuring documents](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Structuring_content/Structuring_documents)
