# Connaissances

## Ce que j'ai appris :
- Le terme redesign
- Différence refacto et redesign

## Ce que je connaissais déjà :
- Le refactoring
- Code Kata

# Questions
# Code Kata
## Qu’est-ce qu’un kata ? A quoi ça sert ?

- Un kata est un terme japonais utilisé pour désigner une forme dans les arts martiaux, un ensemble de mouvements coordonnés et codifiés.
- Dans les arts martiaux japonais, Suite codée de mouvements constituant un exercice d'entraînement à la pureté du geste.
- Dans le contexte de la programmation, cela consiste en un court exercice de programmation visant à améliorer les compétences de l’utilisateur par une pratique répétitive.

## Faire le kata « Gilded Rose » d'Emily Bache (de préférence la version en TypeScript):
- Veuillez trouver ici une première solution simple (mais surtout rapide) en utilisant du TDD :
https://github.com/KevinD-UP/GildedRose-Refactoring-Kata/tree/simple-solution/TypeScript
Cette solution serait à privilégier lorsque nous avons des impératifs business, où il faudrait aller vite. Le défaut ici résidant dans l'anti-pattern `God class` avec un fichier service qui fait tout.

- Ici, une solution plus avancée combinant TDD et principes SOLID (Malheureusement j'ai été tué par le gobelin à l'étage pour avoir toucher à la classe Item dans cette solution):
https://github.com/KevinD-UP/GildedRose-Refactoring-Kata/tree/more-advance/TypeScript
Le défaut de cette solution est sa complexité et le temps de mise en place qui ne pourrait pas convenir aux impératifs business. Mais elle est plus facilement extensible si à l'avenir de nouveau type de produit viendrait à s'ajouter. Elle a également comme propriété de résoudre l'anti-pattern `domain anemic` car chaque objet embarque un comportement avec lui là ou avait l'objet Item se contentait de contenir uniquement des données.

## Lorsque vous êtes satisfait de votre travail, regarder la vidéo de David Gageot. Vous n’êtes pas obligé de rédiger une réponse mais vous pouvez mentionner un point que vous souhaiteriez aborder en séance.
- Comment concilier efficacement refacto et impératif business

# Refactoring
## Quelle est la différence entre un refactoring et un redesign ?
### Motivation
- Un refactoring a pour objectif de rendre le code plus compréhensible et lisible.
- De l'autre côté, on redesign lorsque qu'on a besoin de changer une fonctionnalité ou lorsqu'on prépare le code à être étendu.

### Complexité
- Chaque refacto est un changement mineure dans le code, comme le renommage d'une méthode. Chaque changement doit être atomique de sorte à ce que chacun d'entre eux apporte de la valeur mais où on peut se stopper à n'importe quel moment sans avoir un impact négatif sur la codebase

- De l'autre côté un redesign ne doit pas être fait sans un plan, il faut savoir où on va et on ne peut pas s'arrêter jusqu'à l'arrivé. Un redesign est terminé lorsque le plan est achevé.

### Scope
- Le point de départ d'un refacto est une classe ou une méthode. On peut les renommer, les extraires dans une classe différente mais la portée du changement ne doit pas excéder 2 ou 3 fichiers.

- De l'autre côté le redesign concerne plutôt la communication entre les objets et leurs interactions. Cela signifie qu'un redesign affecte plusieurs plusieurs classes et comment elles communiquent

### Timing
- Il faut refactorer sur une base quotidienne, que ça soit sur de nouvelles fonctionnalités ou lorsque qu'on modifie quelque chose d'existant. Pendant notre tâche, nous remarquons une partie du code et nous décidons spontanément de la refactorer. Ce n'est donc pas une tâche principale mais additionnelle.

- Au contraire, lorsqu'on redesign, cela est un objectif. Il se peut également que durant le redesign, nous effectuons quelques refacto.

## A quel moment pensez-vous qu’il faille refactorer du code ?
- Voir la section timing juste au dessous.

## Décrire très succinctement (2 lignes max) 3 patterns de refactoring.
- Retourner la comparaison directement plutôt qu'un booléen en fonction de la comparaison.
```TypeScript
// NON
function isOrange(color) {
  if (color === "orange") {
    return true;
  } else {
    return false;
  }
}
// OUI
function isOrange(color) {
  return color === "orange";
}
```
- Choisir la bonne boucle, notamment dans le cas ou nous n'aurions pas besoin de l'index.
```TypeScript
// NON
for (let i = 0; i < array.length; i++)

// OUI
for (let element of array)
```
- Stocker les conditions complexes dans des variables.
```TypeScript
// NON
function example(bool1, bool2, bool3){
    if ((bool1 && bool2) || (bool1 && !bool2 && !bool3 || (!bool1 && bool2)) || (bool1 && bool2 && bool3)) {
        return true
    }
    return false
}

// OUI
function example(bool1, bool2, bool3){
    const myComplexCondition = bool1 && bool2) || (bool1 && !bool2 && !bool3 || (!bool1 && bool2)) || (bool1 && bool2 && bool3)
    if (myComplexCondition) {
        return true
    }
    return false
}
```

## Comment rendre votre code facile à refactorer ?
- Un code facile à refactorer devrait être un code suivant les principes SOLID. Ainsi nous sommes plus facilement capable de comprendre ce que fait chaque classe et méthode. Dans l'idéal, ce code devrait également être accompagné de test de sorte à ce que grâce à la méthode TDD, nous pouvons nous assurer que le refacto ne change pas le comportement de l'objet ou de la méthode et éviter la régression.

# Sources
- https://wikidiff.com/refactor/redesign
- https://www.quora.com/What-is-the-difference-among-refactoring-re-architecting-redesign-and-rewriting
- https://embeddedcomputing.com/technology/processing/eda-tools/verifying-your-code-when-refactoring-or-redesigning-that-is-the-question
+ Source du sujet.

# Difficultés

- Aucune
