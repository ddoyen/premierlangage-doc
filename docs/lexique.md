# Index des clés et lexiques des termes de Premier Langage


## A


### author (clé optionnelle)

La valeur de cette `clé` permet de spéficier un auteur ou plusieurs auteurs. Comme dans toute
communauté, l'auteur d'une ressource est toujours un bon juge pour en arbitrer les améliorations
proposés par la communauté. C'est une saine pratique de préciser les auteurs.


## B


### before (clé associé au builder before)

Losqu'une ressource utilise le [builder `before`](before.md), elle doit alors absolument 
définir une clé `before`. Cette balise, souvent sur plusieurs lignes, devra contenir un 
petit script Python exécuté une seule fois à la construction.


### builder (clé optionnelle)

Le builder est un programme python exécuté avant que l'exercice soit proposer à l'apprenant.
Le builder sert à rendre les exercices plus dynamiques notament en y insérant des parties
aléatoires. Sans builder déclaré dans une ressource, l'étape de construction consiste juste 
à ne rien faire


## C


### codebefore (Clé associé au template stdsandboxC)

Dans le template `stdsandboxC`, `codebefore` est utilisé pour inclure du code avant le code
réponse proposé par l'apprenant. Si par exemple, l'exercice en C demande d'écrire une fonction
utilisant une nouvelle structure `Node`, alors pour une bonne compilation, la définition de cette 
structure doit être insérer avant le code rendu par l'apprenant. `codebefore` permet de faire 
cette discrète insertion.


### codeafter (Clé associé au template stdsandboxC)

Dans le template `stdsandboxC`, la clé `codeafter` permet de rajouter du code C à la suite du 
code proposé par l'apprenant et cela avant compilation. Quand un exercice demande de coder une
fonction et que les tests mettent en jeu un programme, `codeafter` permet à l'enseignant de 
rajouter une fonction main permettant de tester correctement le code rendu par l'apprenant.


## E


### extend (clé optionnelle)

La balise extend permet d'importer automatiquement des informations issus d'un template ou 
encore d'un autre exercice. C'est comme une inclusion ou encore un copier coller. Tout ce qui 
se trouvait dans la source va se retrouver dans la cible et il reste toutefois possible de 
redéfinir les valeurs des clés importées. C'est ce qu'on appelle l'héritage (de manière générale 
en informatique). La cible hérite de la source. C'est très puissant dans le sens que ça permet
de créer très rapidement des clônes, puis de modifier les clônes créés.

Voici un exemple :
```python
  # ceci est dans le fichier deuxieme.pl 
  extend= premier.pl 
```
La ligne précédente a pour effet d'ajouter dans le dictionnaire de l'exercice 
_deuxieme_ les clefs de l'exercice _premier_.


## F

### form (clé obligatoire)

Le formulaire de l'exercice. L'idée est que l'on veux une action de l'utilisateur et donc que l'on souhaite lui fournir des input html pour cela. La gestion de la form est laissé à PL il vous suffit de définir les **input** souhaités dans la balise form. Par exemple pour une response textuelle simple:
```python
form==
<input type="text" name="form_answer" >
==
```


## G


### grader (clé obligatoire)

Dans Premier Langage, on désigne par le terme de grader le programme Python qui doit corriger
les réponses de l'apprenant. Le grader assure en fait deux missions :

* Il établit une note entre 0 et 100 en analysant les réponses de l'apprenant.
* Il prépare des feedbacks adaptés suivant les réponses de l'apprenant.

La clé `grader` est donc obligatoire dans tout exercice PL. Soit le grader est définit sur
place localement dans l'exercice mais comme l'écriture d'un grader demande un peu d'expérience
avec PL, le plus simple est souvent d'utiliser un template pour hériter de son grader.


## S

### sandboxio.py (Module utilitaire pour fabriquer un nouveaux grader (niveau avancé))

sandboxio.py est un module Python pour les utillisateurs experts voulant coder leur propre
grader. A minima, ces personnes doivent être capable de produire du code et donc de programmer
en Python. Pour être précis, sandboxio.py est un module qui propose trois fonctions A.P.I.
pour écrire un grader. Dans le but de vous éviter d'importer les bilbiothèques sys et json, les
trois fonctions de sandboxio.py vont gérer pour vous les entrées/sorties et la restitution au
système du couple (note, feedback) tout en updatant le contexte au besoin. Un grader écrit en
utilisant les entrées/sorties définies avec sandboxio.py a toute les chances d'être PL-compatible.


### solution (Clé associé au template stdsandboxC)

Dans le template `stdsandboxC`, la clé `solution` permet de définir une solution enseignant
invisible pour les apprenants. Le contenu de cette clé est alors utilisé par le template pour
auto-générer les sorties attendues des tests.


## T


### title (clé obligatoire)

La valeur associé à la clé `title` donne un titre à l'exerice PL. Si vous définissez cette balise
dans une activité, alors vous lui spécifierez un titre. Un bon titre est juste une chaîne de caratères.
Un bon titre décrit simplement le contenu de l'exercice. Les bons titres facilite les recherches et la
réutilisabilité des ressources.


### template (clé optionnelle)

Même chose que la baslise [extends](./#extends)
Extends est en fait plus général (extends permet d'hériter de n'importe quel type de ressource). Si
vous souhaitez hériter d'un template, alors utiliser plutôt la clé template que la clé extends, c'est
plus propre et plus clair, vous spécifié alors vraiment votre ressource comme étant un certain 
type d'exercice.


### text (clé obligatoire)

La clé `text` est très souvent définie sur plusieurs ligne. La balise à vocation à contenir 
le corps de l'énoncé de l'exercice dans un exercice PL. C'est donc l'ensemble des consignes
que vous souhaitez transmettre à votre apprenant avant qu'il remplisse le formulaire de 
l'exercice et qu'il soumette sa réponse. 
