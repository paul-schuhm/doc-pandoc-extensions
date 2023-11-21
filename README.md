# Utiliser les extensions de pandoc

- [Utiliser les extensions de pandoc](#utiliser-les-extensions-de-pandoc)
  - [Lister les extensions](#lister-les-extensions)
  - [Expliciter les formats d'entrée et de sortie](#expliciter-les-formats-dentrée-et-de-sortie)
  - [Activer/Désactiver une extension](#activerdésactiver-une-extension)
  - [Markdown vers Markdown sans commentaires, avec l'option `--strip-comments`](#markdown-vers-markdown-sans-commentaires-avec-loption---strip-comments)
  - [Markdown vers PDF](#markdown-vers-pdf)
  - [Markdown avec des expressions mathématiques](#markdown-avec-des-expressions-mathématiques)
  - [Une commande utile](#une-commande-utile)
  - [Références](#références)


Un peu de documentation sur l'usage plus avancé de pandoc et de ses extensions. Quelques templates utiles sont également présentés pour publier vers du HTML et PDF avec des expressions mathématiques.

## Lister les extensions

~~~bash
#Liste toutes les extensions
pandoc --list-extensions
#Liste les extensions pour le format markdown
pandoc --list-extensions=markdown
~~~

Les extensions indiquées avec un `+` sont activées par défaut, un `-` sont désactivées par défaut.

## Expliciter les formats d'entrée et de sortie

Liste tous les formats d'entrée et de sorties gérés par pandoc

~~~bash
pandoc --list-input-formats
pandoc --list-output-formats
~~~

Pour expliciter le format d'entrée, utiliser l'option `-f/--from`, pour le format de sortie `-t/--to`

~~~bash
#Convertir hello.txt du markdown vers LaTeX (sur la sortie standard)
pandoc -f markdown -t latex hello.txt
#Convertir un fichier html vers du markdown
pandoc -f html -t markdown index.html
~~~

## Activer/Désactiver une extension

Pour activer ou désactiver une extension, indiquer respectivement le format suivi d'un `+` ou `-` suivi du nom de l'extension

~~~bash
#Activer l'extension tex_math_single_backslash
pandoc -f markdown+tex_math_double_backslash -t html5 -o output.pdf test-document.md --mathml
#Désactiver les footnotes
pandoc -f markdown-footnotes -t html5 -o output.pdf test-document.md  
~~~

## Markdown vers Markdown sans commentaires, avec l'option `--strip-comments`

Très utile pour garder ses sources commentées et publier au format markdown (publié sur un dépôt par exemple) sans ses commentaires

~~~bash
pandoc -f markdown -t markdown --strip-comments test-document.md -o test-document-without-comments.md
#ou plus compactement
pandoc --strip-comments test-document.md -o test-document-without-comments.md
~~~

## Markdown vers PDF

Publication en passant par le format HTML (pour appliquer une feuille de style CSS)

~~~bash
pandoc test-document.md -t html5 -o output-via-html.pdf --css style.css
~~~

Publication directement avec pdflatex (LateX like)

~~~bash
pandoc test-document.md --pdf-engine=pdflatex -o output-via-pdflatex.pdf
~~~

> En utilisant pdflatex, on a naturellement accès aux expressions mathématiques LateX.

## Markdown avec des expressions mathématiques

Plusieurs options :

- [MathML](https://www.w3.org/Math/), MathML is a low-level specification for mathematical and scientific content on the Web and beyond, publié par le W3C. Supporté par les browsers et les lecteurs e-books.
- [mathjax](https://www.mathjax.org/)

Publication en passant par le format HTML (pour appliquer une feuille de style CSS) avec mathml :

~~~bash
#Avec l'option mathml
pandoc test-document.md -t html5 -o output.pdf --mathml
#Avec l'option mathml et block double backslash (recommandé)
pandoc -f markdown+tex_math_double_backslash -t html5 -o output.pdf test-document.md --mathml
~~~

## Une commande utile

Publier le fichier markdown `source.md` vers PDF `output.pdf` avec expressions et blocs mathématiques TeX (inline et display) et une feuille de style CSS :

~~~bash
pandoc -f markdown+tex_math_double_backslash -t html5 -o output.pdf source.md --mathml --css=style.css
~~~

Voir le fichier [`template.md`](./template.md) pour un récapitulatif d'un document type utile, ainsi que [sa feuille de style](./style.css).

## Références

- [Site officiel de pandoc](https://pandoc.org)
- `man pandoc` : pages de manuel de pandoc
- [Pandoc manual : Extensions](https://pandoc.org/MANUAL.html#extensions)
- [Pandoc manual : Syntax highlighting](https://pandoc.org/MANUAL.html#syntax-highlighting), pour mettre en exergue le code source dans différents langages et options