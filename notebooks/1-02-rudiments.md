---
celltoolbar: Slideshow
ipub:
  sphinx:
    toggle_input: true
    toggle_input_all: true
    toggle_output: true
    toggle_output_all: true
jupytext:
  cell_metadata_filter: all
  formats: ipynb
  notebook_metadata_filter: all,-language_info,-toc,-jupytext.text_representation.jupytext_version,-jupytext.text_representation.format_version
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Python 3
  language: python
  name: python3
notebookname: le langage Python
rise:
  autolaunch: true
  slideNumber: c/t
  start_slideshow_at: selected
  theme: sky
  transition: cube
version: '1.0'
---

+++ {"slideshow": {"slide_type": "slide"}}

<div class="licence">
<span>Licence CC BY-NC-ND</span>
<span>Thierry Parmentelat</span>
<span><img src="media/inria-25-alpha.png" /></span>
</div>

+++ {"slideshow": {"slide_type": ""}}

# le langage Python

+++ {"slideshow": {"slide_type": "slide"}}

## commentaires

tout ce qui est après un `#` est un commentaire,  
et sera ignoré par l'interpréteur Python

```{code-cell}
# ceci est un commentaire

10 * 10   # et ici aussi
```

+++ {"slideshow": {"slide_type": "slide"}}

## nombres

```{code-cell}
:cell_style: split

# entiers 
10
```

```{code-cell}
:cell_style: split

# flottants
3.14
```

```{code-cell}
:cell_style: split

# complexes
1j * (2+4j)
```

```{code-cell}
:cell_style: split

# booléens True et False
True
```

+++ {"slideshow": {"slide_type": "slide"}}

## variables

pour définir une variable, il suffit de l'affecter avec le signe `=`

```{code-cell}
---
cell_style: split
slideshow:
  slide_type: ''
---
# remarquez que ceci n'affiche rien
a = 10
```

```{code-cell}
:cell_style: split

# l'utilité c'est bien sûr 
# de garder un résultat pour
# s'en reservir ensuite
a + a
```

+++ {"slideshow": {"slide_type": "slide"}}

## fonctions

on définit une fonction avec le mot-clé `def`

```{code-cell}
:cell_style: split

# on définit une fonction en donnant un nom
# aux paramètres
# 
# à nouveau ici on ne va rien afficher
def P(x):
    return x**2 + 3*x + 2
```

```{code-cell}
:cell_style: split

# mais on peut maintenant
# appeler la fonction P
P(10)
```

```{code-cell}
:cell_style: split

P(100)
```

+++ {"slideshow": {"slide_type": "slide"}}

## mots clés

+++ {"cell_style": "center"}

un certain nombre de mots sont réservés ;  
ce sont les "mots-clé" du langage   
on ne peut pas les utiliser comme noms de variable

+++ {"cell_style": "split"}

```python
# ceci provoque une erreur
if = 2 

  File "<ipython-input>", line 3
    if = 2
       ^
SyntaxError: invalid syntax
```

+++ {"cell_style": "split"}

| **liste**    |   &nbsp; | &nbsp;  | &nbsp;       | &nbsp; |
|----------:|---------:|--------:|-------------:|-------:|
| False | await | else    | import       | pass   |
| None  | break    | except  | in           | raise  |
| True  | class    | finally | is           | return |
| and       | continue | for     | lambda       | try    |
| as        | def      | from    | nonlocal | while  |
| assert    | del      | global  | not          | with   |
| async | elif     | if      | or           | yield  |

+++ {"slideshow": {"slide_type": "slide"}}

## importer une librairie

+++

certaines fonctionnalités sont disponibles au travers  
de bibliothèques, auxquelles on peut accéder en les important

```{code-cell}
import math
```

```{code-cell}
# attention cette façon d'obtenir de l'aide est 
# spécifique à IPython / notebooks
# avec un interprète Python standard, on ferait 
# help(math)
math?
```

+++ {"slideshow": {"slide_type": "slide"}}

## utiliser une librairie

une bibliothèque expose typiquement un certain nombre de symboles  
par exemple dans `math` on va trouver

* `pi` une variable qui dénote le nombre $\pi$
* `sin` une fonction qui sait calculer le sinus

pour accéder à ces symboles on utilise la notation `.`

```{code-cell}
:cell_style: split

math.pi
```

```{code-cell}
:cell_style: split

# ça devrait être 0 mais ...
math.sin(math.pi)
```

+++ {"slideshow": {"slide_type": "notes"}}

Remarquez qu'ici on devrait obtenir 0, mais les calculs sur les flottants sont faits de manière approchée.

+++ {"slideshow": {"slide_type": "slide"}}

## alternative

on peut aussi faire comme ceci

```{code-cell}
:cell_style: split

from math import pi, sin

pi
```

```{code-cell}
:cell_style: split

# idem
sin(pi)
```

+++ {"slideshow": {"slide_type": "notes"}}

Préférez savoir d'où viennent les fonctions que vous utilisez. C'est pourquoi on recommande plutôt d'utiliser, par exemple, la forme `math.sin` plutôt que `sin`, qui garde la trace du module d'où provient le symbole `sin`.

+++ {"slideshow": {"slide_type": "slide"}}

## précision des calculs flottants

bien sûr un flottant est représenté comme une suite de bits 0 ou 1  
cela induit des calculs avec une précision imparfaite

```{code-cell}
# sur les architectures actuelles 
# un flottant est encodé sur 64 bits 
0.2 + 0.1
```

+++ {"slideshow": {"slide_type": "slide"}}

## précision des calculs flottants (option)

+++ {"slideshow": {"slide_type": ""}}

la façon de passer d'un flottant à une séquence de bits  
s'appelle un **encodage** 
[dans le cas des flottants: IEE754](https://en.wikipedia.org/wiki/IEEE_754)  
qui est efficace car supporté par le processeur

+++ {"slideshow": {"slide_type": ""}}

pour faire court - dans le cas le plus courant (`binary64`)  
la précision des calculs est de l'ordre de $10^{-15}$ 


voir un [convertisseur en ligne](http://www.binaryconvert.com/convert_double.html) pour visuels

+++ {"slideshow": {"slide_type": "slide"}}

## booléens

```{code-cell}
:cell_style: split

True
```

```{code-cell}
:cell_style: split

False
```

+++ {"slideshow": {"slide_type": "slide"}}

## texte (chaines)

```{code-cell}
:cell_style: split

# un texte est entre deux '

texte1 = 'bonjour le monde'
print(texte1)
```

```{code-cell}
:cell_style: split

# ou si on préfère entre "

texte2 = "bonjour le monde"
print(texte2)
```

```{code-cell}
:cell_style: split

# comme ça on peut insérer un "

print('Python est un langage "typé"')
```

```{code-cell}
:cell_style: split

# ou un '

print("Python est un langage 'typé'")
```

+++ {"slideshow": {"slide_type": "slide"}}

## `print()`

remarquez qu'on a utilisé la fonction `print` qui est prédéfinie  
on peut l'appeler avec autant d'arguments qu'on veut  
  et de n'importe quel type

```{code-cell}
# simplement pour illustration des possibilités d'appel de fonction
# car on va voir plus loin une forme beaucoup plus pratique
# pour faire ce genre de choses
# 
print("la somme de", 12, "et", 13, "vaut", 12+13)
```

+++ {"slideshow": {"slide_type": "slide"}}

## `len()`

+++

il existe une autre fonction prédéfinie très pratique: `len()`  
qui retourne la longeur d'un objet

```{code-cell}
:cell_style: split

# sur une chaine len()
# retourne le nombre de caractères
# 
# remarquez que les guillemets ne comptent pas
len("abc")
```

```{code-cell}
:cell_style: split

# on compte les caractères 
# et pas les octets

len("été")
```

+++ {"slideshow": {"slide_type": "slide"}}

## textes plus longs

si vous avez besoin d'écrire des textes de plusieurs lignes  
utilisez `"""` au lieu de `"`  -- (ou `'''`)

```{code-cell}
:cell_style: split

bafouille = \
"""To be, or not to be: that is the question:
Whether 'tis nobler in the mind to suffer
The slings and arrows of outrageous fortune,"""
```

```{code-cell}
:cell_style: split

print(bafouille)
```

```{code-cell}
:cell_style: split

# idem avec '''
# le changement de ligne compte 
# pour un caractère (newline) 
court = '''a
b'''
```

```{code-cell}
:cell_style: split

print(court)
```

```{code-cell}
:cell_style: split

# les caractères sont 'a', '\n', et 'b'
len(court)
```

+++ {"slideshow": {"slide_type": "slide"}}

## formatage

pour construire des chaines lisibles,  
le plus simple est la *f-string*

```{code-cell}
:cell_style: split

# une f-string se présente comme une chaine 
# mais préfixée par un f collé
# avant le guillement ouvrant
# qui peut être ' ou " 
f"une f-string"
```

```{code-cell}
:cell_style: split

# l'intérêt est qu'on peut 
# alors insérer des variables
# directement dans la chaine
# en les mettant entre {}

print(f'pi = {pi}')
```

```{code-cell}
# à l'intérieur des {} on peut faire des calculs
print(f"pi = {pi} et sin(pi) = {sin(pi)}")
```

+++ {"slideshow": {"slide_type": "slide"}}

## formatage - suite

il y a des tas de possibilités pour affiner la façon  
dont les données sont mises en forme  
pour cela ajouter un format dans les `{}` avec un `:`  
par exemple pour afficher deux chiffres après la virgule :

```{code-cell}
:cell_style: split

print(f"bla {2*math.pi:.2f} bla")
```

+++ {"cell_style": "split"}

![](media/f-string.svg)

+++ {"slideshow": {"slide_type": "slide"}}

## méthodes sur les chaines

on reviendra plus tard sur la notion de méthode  
mais pour l'instant vous pouvez aller consulter la doc  
  https://docs.python.org/3/library/stdtypes.html#string-methods
qui donne la liste des méthodes disponibles sur les chaines

```{code-cell}
:cell_style: split

# une méthode s'utilise comme ceci

chaine = "bonjour"

chaine.capitalize()
```

```{code-cell}
:cell_style: split

# avec paramètres si besoin

# par exemple, cette méthode 
# sert à centrer en précisant
# avec quoi remplir

chaine.center(13, '-')
```

+++ {"slideshow": {"slide_type": "slide"}}

deux méthodes très utiles sur les chaines : `split` et `join`

```{code-cell}
longue_chaine = "une liste de mots à découper"
```

```{code-cell}
:cell_style: split

# sert à découper une chaine 
# en morceaux

mots = longue_chaine.split()
mots
```

```{code-cell}
:cell_style: split

# et avec join on peut réassembler

"+".join(mots)
```
