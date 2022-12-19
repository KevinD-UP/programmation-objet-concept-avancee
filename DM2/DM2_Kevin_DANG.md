# Connaissance

## Ce que j'ai appris :
- Programmation réactive et Reactive Manifesto
- callback Hell

## Ce que je connaissais déjà :
- Programmation asynchrone en javascript/typescript
- Sucre syntaxique
- Migrations de données et ORM
- Design Pattern

# Questions
# Les promises et la syntaxe async/await
## Pourquoi et dans quels cas est-il considéré comme préférable d'utiliser une promise, plutôt que de bloquer sur un appel IO, alors que le code est plus compliqué à comprendre ?
- Il est préférable d'utiliser une promesse lorsqu'on souhaite réaliser une action qui va prendre du temps comme un appel IO sans bloquer le processus principal, il n'est pas souhaitable de geler le programme.
Nous pouvons également utiliser plusieurs promesses afin de résoudre parallèlement plusieurs opérations toujours sans bloquer le thread principal.

## Comment ré-écrire le code suivant avec des callbacks ? Avec des promises ? Avec la syntaxe async/await ? Attention, les fonctions f1, f2, f3, f4 sont bloquantes, ce qu’on veut éviter.
```typescript
const r1 = f1()
const r2 = f2(r1)
const r3 = f3(r1)
const r4 = f4(r2, r3)
console.log(r4)
```

Avec callbacks

```typescript
f1(r1 => {
    f2(r1, r2 => {
        f3(r1, r3 => {
            f4(r2, r3, r4 => {
                console.log(r4)
            })
        })
    })
})
```

Avec promises
```typescript
const p1 = new Promise((resolve) => resolve(f1()))
p1.then((r1) => {
const r2 = new Promise((resolve) => resolve(f2(r1)))
const r3 = new Promise((resolve) => resolve(f3(r1)))
Promise.all([r2, r3]).then((responses) => console.log(f4(responses[0], responses[1])))
})
```

Avec Async/Await
```typescript
(async() => {
const r1 = f1()
const [r2, r3] = await Promise.all([f2(r1), f3(r1)])
const r4 = f4(r2, r3)
console.log(r4)})()
```
Note: Je considère que la signature des fonctions f1, f2, f3, f4 ont été modifiés en conséquence (exemple: ajout du callback)

## Qu’appelle-t-on un « sucre syntaxique » ? Quel sucre syntaxique avez-vous utilisé sur l’exercice précédent ?
- Un sucre syntaxique est une expression imaginée par Peter J. Landin pour désigner les extensions à la syntaxe d'un langage de programmation qui :
    - ne modifient pas son expressivité ;
    - le rendent plus agréable à écrire comme à lire.

- Le sucre syntaxique exprime le fait de donner au programmeur des possibilités d'écriture plus succinctes ou plus intuitives.
- Le sucre syntaxique que nous avons ainsi utilisé est la syntaxe async/await.
Note: En plus d'être un sucre syntaxique, pour l'utiliser au quotidien je dirais même que c'est bien plus que cela. (cf Source.)

## Pourquoi utiliser des promises plutôt que des callbacks ?
- Afin d'éviter le callback Hell ou pyramid of doom, phénomène de certains codes devenus imprévisibles à cause d'une longue chaine de fonction de rappel.

## Dans quelle mesure les promises sont-elles utiles pour réaliser des systèmes « réactifs » (comme définis dans le « Reactive Manifesto ») ?
- Selon le Reactive Manifesto, les systèmes réactifs doivent être :
    - Disponibles
    - Résilients
    - Souples
    - Orientés Messages

- Ainsi l'utilisation de promesses (mais plus généralement la programmation asynchrone) signifie que le code s'exécute dans une boucle d'événements. Lorsqu'il y a une opération de blocage, l'événement est lancé. Le code de blocage continue de s'exécuter sans bloquer le thread d'exécution principal. Lorsque le code de blocage termine son exécution, il met en file d'attente le résultat des opérations de blocage et les repousse dans la pile.
- Nous avons donc un système réactif disponible car en executant les tâches en fond, le système peut continuer à répondre rapidement et en toute circonstance.
- De plus, un système réactif résilient : En cas de panne le système tout entier ne crash pas et l'erreur est traité au niveau de la promesse.
- Le système est également souple, le traitement "en parallèle" des opérations permet de ne pas ralentir le processus principal, et donc de ne pas avoir un comportement saccadé du système
- Le Reactive Manifesto met en avant l’utilisation de messages asynchrones entre les différentes briques logicielles. On isole ainsi le fonctionnement de chaque composant. On assure un couplage “lâche” entre les éléments qui constituent le système réactif.

# Les migrations de données
## Quel(s) outil(s) permettent de gérer l’accès à la base de donnée et le mapping entre les objets du domaine et les tables stockées en base ?
- Un mapping objet-relationnel (en anglais object-relational mapping ou ORM) est un type de programme informatique qui se place en interface entre un programme applicatif et une base de données relationnelle pour simuler une base de données orientée objet. Ce programme définit des correspondances entre les schémas de la base de données et les classes du programme applicatif. On pourrait le désigner par là, « comme une couche d'abstraction entre le monde objet et monde relationnel ».
Exemple : TypeORM, Prisma, Doctrine

## Quand on veut faire évoluer la structure de la base de données (par exemple, rajouter un champ), il est inenvisageable de supprimer les données et de recréer la base : il faut modifier les données en place. Cette opération se nomme une migration. Quelle solution pouvez-vous mettre en place pour gérer les migrations de données ?
- Pour gérer une migration de données, je ne me base que sur l'ORM utilisé dans le projet. De nos jours les ORM facilite grandement la tâche de la migration même si la façon de migrer dépendra de l'ORM en question TypeORM fonctionnant bien différemment de Prisma.

## Comment tester les migrations ?
- Il est primordial après une migration au minimum de tester la couche Data-Access du projet, c'est à dire là où se trouve nos repositories par exemple, tout ce qui simplifie l'accès à la base de données. Si les choses sont bien faites normalement tout les tests sont automatisés et il faut donc réaliser des tests unitaires, end-to-end ainsi que des tests de non régression.
Si tout les tests passent avec succès nous pouvons conserver la migration sinon un rollback est nécessaire.
A noter qu'ici je ne parle que de l'aspect fonctionnel de l'application. Mais il faudrait également vérifier l'intégrité des données (pas de perte) ou encore la sécurité de la base de donnée après migration par exemple.
De plus il serait judicieux de tester ces migrations d'abord dans d'autres environnements comme par exemple une pré-production avant de faire la migration sur l'environnement de production.

# Design patterns

## Qu’est-ce qu’un design pattern ? Citer les ouvrages qui vous semblent faire référence.
 - un patron de conception (souvent appelé design pattern) est un arrangement caractéristique de modules, reconnu comme bonne pratique en réponse à un problème de conception d'un logiciel. Il décrit une solution standard, utilisable dans la conception de différents logiciels. Il décrit un arrangement récurrent de rôles et d'actions joués par des modules d'un logiciel, et le nom du patron sert de vocabulaire commun entre le concepteur et le programmeur. D'une manière analogue à un motif de conception en architecture, le patron de conception décrit les grandes lignes d'une solution, qui peuvent ensuite être modifiées et adaptées en fonction des besoins.
 - Ouvrages de références :
    - Design Patterns – Elements of Reusable Object-Oriented Software - GoF, Erich Gamma, Richard Helm, Ralph Johnson et John Vlissides
    - Patterns of Enterprise Application Architecture - Martin Fowler
    - Head First Design Patterns: Building Extensible and Maintainable Object-Oriented Software - Eric Freeman, Elisabeth Robson

## Quels sont leurs avantages et leurs limitations ?
### Advantages

- Les patrons de conception sont une boîte à outils de solutions fiables et éprouvées utilisées en réponse à des problèmes classiques de la conception de logiciels. Même si nous n’avons jamais rencontré ces problèmes, le fait de connaitre les patrons est tout de même utile, car il nous enseigne des techniques qui permettent de résoudre toutes sortes de problèmes en utilisant les principes de la conception orientée objet.
- Les patrons de conception définissent un langage commun que chaques développeurs peuvent utiliser pour mieux communiquer. Nous pouvons dire : « Oh, tu n’as qu’à utiliser un singleton. » et tout le monde comprendra instantanément ce que vous venez de suggérer. Nul besoin d’expliquer ce qu’est un singleton, si vous connaissez déjà son nom et son principe.
- Ces avantages sont également toujours valables lors de la maintenance ainsi que durant les futures développement du programme

### Limitation

- Utiliser les design patterns demande beaucoups de connaissances. Avoir des design pattern disponible tend à faire penser que tout les problèmes peuvent se résoudre en les utilisant. En somme, cela peut limiter la créativité et le désire de trouver de nouvelles et meilleurs solutions.
- Bidouilles pour de mauvais langages de programmation : Nous faisons généralement appel aux patrons de conception lorsque l’on choisit un langage de programmation ou une technologie qui ne possède pas un niveau suffisant d’abstraction. Dans ce cas, les patrons deviennent une bidouille qui octroie au langage des super-pouvoirs absolument nécessaires.
Par exemple, le pattern Stratégie peut être implémentée avec une fonction anonyme toute simple (lambda) dans la majorité des langages de programmation modernes. Idem pour le pattern singleton.
- Solutions inefficaces : Les patrons tentent d’automatiser des approches qui sont déjà très largement utilisées. Cette unification est vue par beaucoup comme un dogme, et ils implémentent les patrons « à la virgule près », sans les adapter au contexte de leur projet.
- Utilisation injustifiée : De l'adage, si tout ce que vous avez est un marteau, tout ressemble à un clou.
- C’est le problème qui va hanter les novices qui viennent juste de se familiariser avec les patrons de conception. Maintenant qu’ils les connaissent, ils vont essayer de les appliquer partout, même dans des situations où du code basique aurait fait l’affaire.

## Décrire brièvement 3 design patterns de votre choix.
### Factory
- Factory est un patron de conception de création qui définit une interface pour créer des objets dans une classe mère, mais délègue le choix des types d’objets à créer aux sous-classes.

### Strategy
- Strategy est un patron de conception comportemental qui permet de définir une famille d’algorithmes, de les mettre dans des classes séparées et de rendre leurs objets interchangeables.

### Adaptateur
- Adaptateur est un patron de conception structurel qui permet de faire collaborer des objets ayant des interfaces normalement incompatibles.

# Sources
- https://geekflare.com/fr/javascript-event-loops/#:~:text=La%20boucle%20d'%C3%A9v%C3%A9nements%20est,t%C3%A2ches%20pour%20les%20rappels%20disponibles.
- https://jscomplete.com/learn/the-difference-between-callbacks-and-promises#:~:text=The%20superiority%20of%20promises%20over,blocking%20the%20main%20program%20process.
- https://refactoring.guru/
- https://blog.pragmatists.com/automating-data-migration-testing-db721c34ed09
- https://www.datamigrationpro.com/data-migration-testing-strategy
- https://www.softwaretestinghelp.com/data-migration-testing/
- https://dev.to/neisha1618/callbacks-vs-promises-4mi1
- https://blog.oakbits.com/asyncio-and-rxpy.html
- https://www.organisation-performante.com/le-reactive-manifesto-de-quoi-ca-parle/
- https://www.codemotion.com/magazine/backend/benefits-of-reactive-programming-codemotion-magazine/

# Difficulté

- Le fait d'utiliser d'anciennes méthodes comme les callbacks est un exercice très intéressant mais également très difficile quand nous nous sommes habitués aux async/await.
- Le sujet des systèmes réactifs, et tout ce qui tourne autour de la programmation réactive était très passionant mais également très difficle à prendre en main à comprendre.


