# Document test des extensions de Pandoc

## Heading IDs

[Ceci est un lien vers la section Footnote](#footnotes)

## Maths

$x=1+2$

**The Cauchy-Schwarz Inequality**
$$\left( \sum_{k=1}^n a_k b_k \right)^2 \leq \left( \sum_{k=1}^n a_k^2 \right) \left( \sum_{k=1}^n b_k^2 \right)$$

Cette expression $\sum_{i=1}^n X_i$ est inlinée.

## Inline notes

Here is an inline note.[^1]

## Sub et superscript

Subscript (pas besoin d'extension) : H~2~O

Superscript (pas besoin d'extension) : x^2^

## Task lists

(pas besoin d'extension)

-   [x] Write the press release
-   [ ] Update the website
-   [ ] Contact the media

## Code source

``` js
console.log('Hello, world !')
```

``` php
class Foo{

}
```

## Footnotes

(pas besoin d'extension)

Here's a simple footnote,[^2] and here's a longer one. Lorem ipsum dolor
sit amet, consectetur adipiscing elit. Donec a velit neque. Fusce ac
odio eu sem consectetur elementum. Maecenas hendrerit aliquet blandit.
Duis sollicitudin, justo eget maximus lobortis, justo leo gravida
lectus, posuere pellentesque nibh turpis id enim. Aenean luctus id ipsum
et mattis. Vestibulum ante ipsum primis in faucibus orci luctus et
ultrices posuere cubilia curae; Etiam maximus at tellus at malesuada.
Nullam laoreet diam ut semper vestibulum. Vivamus turpis turpis,
interdum quis nisi at, lobortis finibus ante. Nunc sed venenatis urna.
Maecenas ultricies nisl vitae sem pharetra, id commodo ante condimentum.
Mauris ullamcorper lorem vel tincidunt tristique. Pellentesque habitant
morbi tristique senectus et netus et malesuada fames ac turpis egestas.
Quisque pellentesque ligula bibendum, tempus orci ut, dignissim nibh.
[^3]

## Extensions

### fenced_divs (activée par défaut)

Permet d'ajouter des id (avec #) et classes (avec .) pour les documents
HTML

::: {#special .sidebar}
Here is a paragraph.

And another.
:::

Fenced divs can be nested. Opening fences are distinguished because they
must have attributes:

::: Warning
This is a warning.

::: Danger
This is a warning within a warning.
:::
:::

[^1]: Inline notes are easier to write, since you don't have to pick an
    identifier and move down to type the note.

[^2]: This is the first footnote.

[^3]: Here's one with multiple paragraphs and code.

    Indent paragraphs to include them in the footnote.

    `{ my code }`

    Add as many paragraphs as you like.
