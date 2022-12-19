# Connaissances

## Ce que j'ai appris :
- Asana, CircleCI, Travis, Waffle, PyPI, Nexus, Artifactory.

## Ce que je connaissais déjà :
- Jenkins, Jira, trello, Docker Hub, npm, yarn, Sonarqube, Gradle, Maven, Docker Hub, Azure.
- Les besoins d'une documentation complète
- Différence type/interface
- Syntaxe ReturnType et TypeOf


# Questions
# Quelques outils
## Pour les outils suivants couramment utilisés dans l’industrie logicielle, déterminer leur usage et à quoi ils correspondent dans GitLab : jenkins, asana, circleCI, Jira, trello, travis, waffle.io, Azure DevOps.

- Jenkins : Jenkins est un outil open source de serveur d'automatisation. Il aide à automatiser les parties du développement logiciel liées au build, aux tests et au déploiement, et facilite l'intégration continue et la livraison continue. Equivalent au GitLab CI/CD
- Asana : Asana est un gestionnaire de communication d'équipe. Le produit prend en charge de nombreuses fonctionnalités, notamment les espaces de travail, des projets, des tâches, des étiquettes, des notes, des commentaires et une boîte de réception qui organise les mises à jour des informations en temps réel. Equivalent au board Kanban de Gitlab
- CircleCI : CircleCI est une plate-forme d'intégration continue et de livraison continue qui peut être utilisée pour mettre en œuvre des pratiques Devops. Equivalent au Gitlab CI/CD
- Jira : Jira est un système de suivi de bugs, de gestion des incidents et de gestion de projets. Equivalent au board Kanban de Gitlab
- Trello : Trello est un outil de gestion de projet en ligne inspiré par la méthode Kanban. Il repose sur une organisation des projets en planches listant des cartes, chacune représentant des tâches. Equivalent au board Kanban de Gitlab
- Travis : Travis CI est un logiciel libre d'intégration continue. Il fournit un service en ligne utilisé pour compiler, tester et déployer le code source des logiciels développés, notamment en lien avec le service d'hébergement du code source GitHub. Equivalent au Gitlab CI/CD
- Waffle.io : Waffle.io était un outil de gestion de projet en ligne. Equivalent au board Kanban de Gitlab
- Azure DevOps : Azure DevOps est une solution d’intégration continue avec un environnement hébergé dans le cloud Azure qui permet de planifier les développements, versionner le code source avec Git, automatiser la construction et le déploiement des applications, lancer des scénarios de test et tracer les anomalies rencontrées dans ces processus. Equivalent à Gitlab.

## Quel est sont les différences / les similarités entre maven, PyPI, sonarqube, gradle, nexus, docker hub, artifactory, yarn, npm ?
D'abord une définition de chaque afin de ne pas nous perdre :

- Maven : Apache Maven est un outil de gestion et d'automatisation de production des projets. Il est utilisé pour automatiser l'intégration continue lors d'un développement de logiciel. logiciels Java
- PyPI : PyPI est le dépôt tiers officiel du langage de programmation Python. Son objectif est de doter la communauté des développeurs Python d'un catalogue complet recensant tous les paquets Python libres.
- Sonarqube : SonarQube est un logiciel libre de qualimétrie en continu de code. Il aide à la détection, la classification et la résolution de défaut dans le code source, permet d'identifier les duplications de code, de mesurer le niveau de documentation et connaître la couverture de test déployée.
- Gradle : Gradle est un moteur de production fonctionnant sur la plateforme Java. Il permet de construire des projets en Java, Scala, Groovy voire C++.
Gradle allie les atouts de Apache Maven et Apache Ant : il allie l'utilisation de conventions à la manière de Maven (convention plutôt que configuration) avec la flexibilité de Ant pour décrire les tâches de construction, avec une cohérence forte dans l'interface de programmation des tâches.
- Nexus : Nexus un ensemble composé de Nexus Lifecycle, Nexus Firewall, Nexus Container et Nexus Repository. Ces trois composants permettent d'empêcher automatiquement les composants open source défectueux d'entrer dans le cycle de développement logiciel, identifier et contrôler les risques liés aux OSS dans les conteneurs pour protéger le développement et l'exécution et enfin gérer les bibliothèques et stocker les artefacts dans un repository universel, puis les partager avec les équipes de développement.
- Docker Hub : Docker Hub est un service pour rechercher and partager des container images de notre application avec une équipe de développement ou l'ensemble de la communauté. On y trouve de nombreux projet open-source ou des projets d'éditeur de logiciels indépendant qui distribue leur code dans des container.
- Artifactory : Artifactory est un gestionnaire de dépôts d'objets binaires et propose une gestion intégrale des binaires, qui élimine la complexité à faire travailler ensemble différents systèmes de gestion de packages, et apporte de la cohérence au workflow CI/CD.
- npm : npm est le gestionnaire de paquets historique et par défaut pour l'environnement d'exécution JavaScript Node.js de Node.js. npm se compose d'un client en ligne de commande, également appelé npm, et d'une base de données en ligne de paquets publics et privés payants, appelée le registre npm.
- Yarn : Yarn est un nouveau gestionnaire de dépendances pour NodeJS qui propose une approche plus rapide et plus sécurisée que le gestionnaire historique npm.
- Ainsi, à part Sonarqube, tous fournisse un service permettant d'avoir accès facilement à des dépendances externes, leur différences se feront au niveau de la plateforme et langage utilisé (java, python, javascript).
- Toutes ces technologies y compris Sonarqube peuvent être intégré dans un workflow CI/CD, qui facilite grandement le développement d'une application. Sonarqube et Nexus pouvant avoir un role de contrôle de qualité par exemple tandis que npm, yarn ou gradle servent au build de l'application.

## A quels besoin de documentation répondent :
### Le « user manual »
- Le `User manual` est un document fourni à l'utilisateur qui l'aide à utiliser le produit.
Il contient usuellement des instructions étape par étape pour guider l'utilisateur sur l'utilisation du produit et peut le dépanner dans le cas ou quelque chose ne va pas.
Elle répond ainsi à un besoin d'experience utilisateur.

### La référence technique
- La `référence technique` est un document à destination des développeurs. Le but de la documentation technique est d’accélérer les développements de nouvelles fonctionnalités. Le développeur doit donc y trouver son compte et avoir confiance dans ce qu’il lit. Elle doit systématiquement être à jour et claire.
- Elle doit être synchrone avec le code.
- Elle doit être écrite en même temps que le code.
- Elle doit être lisible à partir du code et de l’extérieur : c’est ce qu’on appelle la multidiffusion


### Un tutoriel « getting started »
- Un tutoriel `getting started` s'adresse à une audience de débutant. En effet l'utilisateur débutant ne veut pas perdre de temps sur des détails ou sur une utilisation avancée. Ils veulent pouvoir utiliser le produit ou le service simplement et rapidement dans des cas réel d'usage. Ce tutoriel doit donc les aider à être confortable avec la mise en place et l'utilisation du produit, à comprendre qu'est-ce que le produit ou service leur permet de faire ainsi que les fonctionnalités clés. Un bon tutoriel entretient une relation de confiance entre l'utilisateur et le produit ou service.

## Pour tous les services précédemment cités et lorsque cela s’applique, identifier le lien officiel vers ces trois types de documentations.

### Jenkins
- User manual : https://www.jenkins.io/doc/
- Référence technique : https://www.jenkins.io/doc/developer/
- Getting started : https://www.jenkins.io/doc/book/getting-started/
### Asana
- User manual : https://asana.com/fr/guide/help
- Référence technique : https://developers.asana.com/docs/
- Getting started : https://asana.com/fr/guide/get-started/begin/quick-start
### CircleCI
- User manual : https://circleci.com/docs/
- Référence technique : https://circleci.com/docs/api-developers-guide/
- Getting started : https://circleci.com/docs/getting-started/
### Jira
- User manual : https://www.atlassian.com/fr/software/jira/guides
- Référence technique : https://www.atlassian.com/fr/software/jira/guides/developers/basics
- Getting started : https://www.atlassian.com/fr/software/jira/guides/getting-started/basics
### Trello
- User manual : https://trello.com/fr/guide
- Référence technique : https://developer.atlassian.com/cloud/trello/
- Getting started : https://trello.com/fr/guide/trello-101
### Travis
- User manual : https://docs.travis-ci.com/
- Référence technique : https://developer.travis-ci.com/
- Getting started : https://docs.travis-ci.com/user/for-beginners/
### Waffle.io
- Aucune documentation n'est disponible puisque l'outil n'est plus disponible depuis 2019
### Azure DevOps
- User manual : https://learn.microsoft.com/en-us/azure/devops/user-guide/what-is-azure-devops?toc=%2Fazure%2Fdevops%2Fget-started%2Ftoc.json&bc=%2Fazure%2Fdevops%2Fget-started%2Fbreadcrumb%2Ftoc.json&view=azure-devops
- Référence technique : https://learn.microsoft.com/en-us/azure/devops/dev-resources/?view=azure-devops
- Getting started : https://learn.microsoft.com/en-us/azure/devops/get-started/?view=azure-devops

## Quels services vous ont paru particulièrement bien / mal documentés ?
### Service bien documentés
- Jenkins
- Asana
- CircleCi
- Jira
- Trello
- Travis

### Service mal documentés
- Azure Devops

A noter qu'ici le seul critère qui me fait penser cela est l'interface graphique et la navigation. De nos jours, il y a tellement de règles qui permette de rédiger ce qu'on considère une bonne documentation que finalement pour moi toute les documentations que j'ai pu voir actuellement sont à la fois complet et aussi tous dotés d'une partie getting started absolument nécessaire et pratique.
Si en bonus je voudrais préciser une documentation que je trouve réellement infâme, je dirais la documentation d'AWS.

## Afin de guider vos choix de technologies, de quels aspects tenez-vous plus compte et dans quel ordre ?
- D'abord en priorité les besoins du projet, inutile d'utiliser les frameworks et technologies dernier cri pour un simple CRUD, ne pas se complexifier la tâche pour rien.
- L'aspect open-source ou propriétaire (critère assez personel).
- Date du dernier commit sur master/main ou changelog, pour vérifier que la technologie est toujours maintenue et n'a pas été déprécié.
- Sa popularité (nombre d'étoile sur github par exemple) que je relie à la date de sortie.
Plus une technologies est populaire et daté, plus nous avons de chance de trouver des réponses à des problèmes connu (stack overflow)
- La documentation, qui doit notamment contenir un tutoriel getting started. En effet, la meilleure façon de faire son choix, c'est encore de tester, je souhaite donc pouvoir mettre en place et tester rapidement dans mon projet, chaque technologie qui ont pu passer les 3/4 critères précedents.

# Typescript – Classes, interfaces et types
## Quelles sont les différences entre un type et une interface ? Dans quelles situations une solution est-elle préférable qu’une autre ?
- De nombreuses fonctionnalités sont communes et dans la majorité des cas, les deux sont interchangables mais voici quand même quelques différences qui peuvent faire pencher la balance.
- Ces exemples sont tirés du `Typescript Handbook`.
```typescript
// Une interface peut-être "réouverte"
// et de nouvelles propriétés ajoutés:

interface Mammal {
    genus: string
}

interface Mammal {
    breed?: string
}

const animal: Mammal = {
    genus: "1234",
    // Echoue car breed doit être un string
    breed: 1
}

type Reptile = {
    genus: string
}

// Pour les type, impossible de faire la même chose
// Duplicate identifier 'Reptile'.
type Reptile = {
    breed?: string
}
```
```typescript
// Voici deux exemples pour décrire un objet avec un type et une interface

interface AnObject1 {
    value: string
}

type AnObject2 = {
    value: string
}

// En utilisant type, nous pouvons créer un alias pour les types primitifs

type SanitizedString = string
type EvenNumber = number

// Ce n'est pas possible avec une interface
// An interface cannot extend a primitive type like 'string'; an interface can only extend named types and classes
interface X extends string {

}
```
```typescript
// Les messages d'erreur de compilation vont toujours utiliser le nom d'une interface.

interface Mammal {
    name: string
}

function echoMammal(m: Mammal) {
    console.log(m.name)
}

// e.g. L'erreur ci dessous va toujours utiliser le nom "Mammal"
// pour se référer au type, ce qui est attendu.
echoMammal({ name: 12343 }) // Type 'number' is not assignable to type 'string'. The expected type comes from property 'name' which is declared here on type 'Mammal'

// Le type m ici est exactement le même que mammal mais comme il n'a pas été directement nommé, Typescript ne le mentionnera pas dans le message d'erreur

function echoAnimal(m: { name: string }) {
    console.log(m.name)
}

echoAnimal({ name: 12345 }) //Type 'number' is not assignable to type 'string'. The expected type comes from property 'name' which is declared here on type '{ name: string; }'
```
- Heuristic venant du Typescript Handbook : utiliser `interface` sauf si on a besoin de fonctionnalités de `type` (comme le renommage de primitives, qui peut être utile pour rendre plus clair la signature d'une méthode/fonction)

## Faire le Beginner/Learner Challenge (et optionnellement, le Intermediate/Advanced Challenge) :
### Beginner/Learner Challenge
```typescript
// In prepration for halloween, you've become the shared DJ for
// all your friends. You've set up the system to distribute the music
// using the hip new typeify API/

import {typeifyAPI} from "type-or-treat"

const playlist = [
    "The Legend of Sleepy Hollow by The Monotones.mp3",
    "(It's a) Monster's Holiday by Buck Owens.mp3",
    "Bo Meets the Monster by Bo Diddley.mp3",
    "Purple People Eater Meets the Witch Doctor by The Big Bopper.mp3",
    "Screamin Ball (at Dracula Hall) by The DuPonts.mp3",
    "Batman, Wolfman, Frankenstein, or Dracula by The Diamonds.mp3",
    "Frankenstein Twist by The Crystals.mp3",
    "'Thriller' by Michael Jackson.mp3"
] as const

playlist
// ^?
// TypeScript thinks this is a list of strings, which is true - but can you
// make TypeScript treat the playlist array more "as constants"?

const api = typeifyAPI("my_api_key")
api.connect()

function playSong(song: typeof playlist[number]) {
    api.play(song)
}

playSong("Purple People Eater Meets the Witch Doctor by The Big Bopper.mp3")

// This works great! But it could be a little more resistent to typos, can you
// think of a way to change the `playSong` `song` parameter reuse the "typeof" the
// playlist, so that TypeScript raises an error if there's a typo?

playSong("(It's a) Monster's Holiday by Buck Owens.mp3")
playSong("The Legend of Sleepy Hollow by The Monotones.mp3")
playSong("Batman, Wolfman, Frankenstein, or Darcula by The Diamonds.mp3")
```
### Intermediate/Advanced Challenge
```typescript
// Costume prep time, you figure "why not dress up like
// the antagonists in the Squid Game?", it seems pretty easy
// based on your old Casa de Papel outfit.
// ( https://duckduckgo.com/?q=casa+de+papel&iax=images&ia=images)

// You set aside time to figure out what you're going to need to
// convert the constume and sketch out the potential work to
// give yourself an idea of timescale:

import {search, printer} from "type-or-treat"

const findOldCostume = () => {
    const jumpSuit = search.attic() || search.closet() || search.garage()
    const estimate = 30
    return { jumpSuit, estimate }
}

const createNewMask = (costume: ReturnType<typeof findOldCostume>) => {
    const mask = printer.printMask()
    mask.shape = "circle"
    costume.estimate += 60
    return { ...costume, mask }
}

const createBodyCamera = (costume:  ReturnType<typeof createNewMask>) => {
    const camera = printer.printCamera()
    // It will need painting too
    costume.estimate += 45
    return { ...costume, camera }
}

const assembleCostume = () => {
    return createBodyCamera(createNewMask(findOldCostume()))
}

// Great, this creates an assembly line of all the parts and
// the work you need to do. However, it relies on `any`s which
// makes working with the actual costume a bit ambiguous:

const costume = assembleCostume()
//    ^?

// Can you think of a way to fix the inference without creating
// new `type`s or `interface`s, or replacing the anys with `{ ... }`?

// Ideally this typeof problem can be solved so that you can
// make a change in one of the functions and not need to update the types.

// You'll know it worked when this line raises an error
console.log(`It should take about ${costume.time} minutes`)

// Now that we've got a working pipeline, can you generate a type
// which represents the end-state of assembleCostume so that others
// can re-use it later?

type Costume = ReturnType<typeof assembleCostume>
```

# Sources
- https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#differences-between-type-aliases-and-interfaces
- https://document360.com/blog/creating-a-user-manual/
- https://medium.com/the-apartment/7-things-to-include-in-your-getting-started-guide-8d4c813cd927
- https://documentwrite.dev/blog/how-to-write-a-getting-started-guide/
- https://www.techsmith.fr/blog/creer-le-guide-d-utilisation-parfait/

# Difficultés
- Les différences homonymes ont complexifiés la recherche de documentation, ce qui a rendu l'exercice très intéressant car il fallait absolument éviter le hors-sujet.
- Par exemple Waffle peut maintenant faire référence à un framework de test de contrat intelligent, ce qui semblait hors sujet au vu des autres outils.
