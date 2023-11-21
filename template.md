# Document type

Ce format est un format utile pour publier du markdown vers du HTML et/ou du PDF

- [Document type](#document-type)
  - [Maths](#maths)
  - [Paragraphes custom avec classes CSS et id](#paragraphes-custom-avec-classes-css-et-id)
  - [Publier ce document en PDF](#publier-ce-document-en-pdf)
  - [Publier ce document en HTML](#publier-ce-document-en-html)



## Maths

Voici un bloc mathématique (TeX display math) :

\\[
\left( \sum_{k=1}^n a_k b_k \right)^2 \leq \left( \sum_{k=1}^n a_k^2 \right) \left( \sum_{k=1}^n b_k^2 \right)
\\]

Cette expression $\sum_{i=1}^n X_i$ est inlinée (TeX inline math).

## Paragraphes custom avec classes CSS et id

::: {#special .bg-custom}
Ceci est un fenced div, utilisable avec [l'extension `fenced_divs`](https://pandoc.org/MANUAL.html#extension-fenced_divs), activée par défaut. Doit commencer par au moins 3 semicolons
:::

[This is *some text*]{.class key="val"}

## Publier ce document en PDF

En rajoutant le numéro de ligne, on peut créer un lien vers une ligne du block de code avec l'ancre `#mycode-{numero de ligne}`

~~~{#mycode .bash .numberLines startFrom="0"}
#Ceci est un commentaire
pandoc -f markdown+tex_math_double_backslash -t html5 -o template.pdf template.md --mathml --css=style.css
~~~

## Publier ce document en HTML

~~~{#mycode .bash }
#Ceci est un commentaire
pandoc -f markdown+tex_math_double_backslash -s -t html5 -o template.html template.md --mathml --css=style.css
~~~