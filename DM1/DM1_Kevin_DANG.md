# Connaissance

## Ce que j'ai appris :
- gitstery
- Utilisation de Terraform pour un déploiement dans le cloud (pour la partie travail en groupe)

## Ce que je connaissais déjà :
- Typescript
- Différence Git, Gitlab, Github
- Gitflow et Trunk-based development (Migration progressive dans mon entreprise)
- Le workflow "Rebase and merge" (utilisé dans le cadre de la migration mentionné plus haut)
- Amazon Web Services

# Questions
## Qu’est-ce qu’un type Union en Typescript ?

- Un type `Union` décrit une valeur qui peut être de différents types. On utilise la barre vertical (`|`) pour séparer chaque type
par exemple `number | string | boolean` est le type d'une valeur pouvant être un nombre, une chaîne de caractère ou un booléen.

## Quels sont les différents types de Decorator en Typescript ?
- Il existe des décorateurs de classe, de méthode, d'accesseur, de propriété et de paramètre.

## Typescript est-il nominally-typed ou structurally-typed ?
- Typescript est structurally-typed c'est-à-dire que les types sont identifiés à leurs propriétés plutôt que leurs noms ou alias.
exemple:

```typescript
type Person = {
    name: string;
    race: string;
}

type Animal = {
    name: string;
    race: string;
}

const kevin: Person = { name: "Kévin Dang", race: "Human" }
const smaug: Animal = { name: "Smaug", race: "Dragon" }

const sayName = (person: Person) => console.log(person.name);
sayName(kevin) // Kévin Dang
sayName(smaug) // Smaug

```

Même si nous typons notre fonction comme prenant en argument un type `Person`, le compilateur n'a aucun problème à prendre le type `Animal` en argument.
En effet les deux types partagent les mêmes propriétés.

## Typescript est-il dynamically-typed ou statically-typed ?

- Typescript est statically-typed, des vérifications de typage se déroule durant le processus de compilation avant d'exécuter le programme.

## Qu’appelle-t-on communément un « singleton » ? Comment peut-on implémenter un singleton en Typescript ?

- Un singleton est une classe dont l'instanciation est restreinte à un seul objet. Ainsi le Singleton est un patron de conception de création qui s’assure de l’existence d’un seul objet de son genre et fournit un unique point d’accès vers cet objet.
Il existe plusieurs façon d'implémenter le singleton en typescript, d'abord "à l'ancienne" : 

```typescript
class Singleton {
    private static instance: Singleton;

    /**
     * Le constructeur est privé afin d'éviter toute instanciation avec l'opérateur 'news'
     */
    private constructor() { }

    /**
     * La méthode statique qui contrôle l'accès à l'instance du singleton
     */
    public static getInstance(): Singleton {
        if (!Singleton.instance) {
            Singleton.instance = new Singleton();
        }

        return Singleton.instance;
    }

    /**
     * La business logic du singleton
     */
    public someBusinessLogic() {
        // ...
    }
}

```
Sinon si le projet utilise un container d'inversion de contrôle comme Inversify, la syntaxe s'en retrouve simplifié:
```typescript
import { Container } from 'inversify'

const container = new Container()
export class Singleton {
    //...
}

container.bind(Singleton).toSelf().inSingletonScope()
```
Tout composant utilisant cette classe `Singleton` comme dépendance disposeront de la même instance.

## Quelle est la différence entre git, GitLab et GitHub ?

- `Git` est un logiciel de gestion de versions décentralisé.
`GitHub` et `Gitlab` sont des services web d'hébergement et de gestion de développement de logiciels, utilisant le logiciel de gestion de versions Git.
Ces deux services proposent des fonctionnalités similaires mais il existe quelques différences, par exemple gitlab comprend des outils d'intégration continue ce qui n'est pas le cas de Github.
Les flux de travail recommandés ne sont également pas les mêmes.

## Quelle est la différence entre « git merge » et « git pull » ?
- La commande `git merge` permet de sélectionner les lignes de développement indépendantes créées avec git branch et de les intégrer à une seule branche.
La commande `git pull` est utilisée pour faire un fetch du contenu d'un dépôt distant et pour le télécharger, puis pour mettre à jour immédiatement le dépôt local qui correspond à ce contenu.
Dans les faits, la commande `git pull` execute en fait `git fetch` (télécharge le contenu du dépôt distant spécifié) suivi de `git merge`

## Vous souhaitez travailler sur une task, puis intégrer votre code à la branche d'intégration. Le merge se fait sur l'UI GitLab après review. Remettre les commandes suivantes dans l'ordre :

### Arrivé sur le projet, mis à jour en local et création de sa branche
```
$ git checkout master
$ git pull
$ git checkout -b my-branch
```

### Partie où finalement le développeur code
```
$ nano my-file
$ git add my-file
$ git commit -m "My commit"
$ git push --set-upstram origin my-branch
```

### Mis à jour de sa branche avec les commits de master dans le cas ou d'autres merges request ont été validé.
```
$ git rebase origin/master
$ git push --force-with-lease
```

### Partie review (je considère ici que la review a été validé par un autre développeur et que l'User story a bien été testé fonctionnellement par un Product Owner par exemple)
- #review sur gitlab
- #merge sur gitlab

### Dans le cas ou notre merge request est validé, nous pouvons remettre à jour le projet en local puis supprimer notre branche.
```
$ git checkout master
$ git pull
$ git branch --delete my-branch
```

Note: Il me semble que plusieurs ordres peuvent être techniquement possibles en fonction des habitudes et des philosophies, c'est pourquoi j'ai voulu détailler cette ordre là.
Par exemple on pourrait considérer faire la review -> rebase -> merge dans cette ordre, c'est quelque chose de tout à fait possible si nous sommes capable de faire confiance yeux fermés en notre intégration continue.
C'est-à-dire que si des conflits sont soulevés par le rebase puis corrigé, l'intégration continue permettra de tester si la résolution de conflit est correct ou pas.
Dans le cas contraire (cf l'ordre que j'ai choisi) où l'intégration continue et donc les tests de la pipeline (qu'ils soient unitaires ou de bout en bout) ne sont pas 100% fiables, personnellement je pense que la branche de développement doit toujours être constamment à jour avec master avec un historique propre et tout conflits résolus pour la review et les tests.
Cela évite de devoir réiterer les procédures de test si des conflits sont soulevés lors du rebase.
Après, encore une fois, est-ce au rôle du reviewer de vérifier que les conflits ont été résolu de la façon correct ? Je pense que tout dépend de la philosophie de l'équipe à ce moment.

## Qui est le coupable ? https://github.com/nivbend/gitstery
- Le coupable est "Cosmo Siwkonk"

## Quelle est la différence entre « Gitflow » et le « Trunk-based development » ?
- Le développement basé sur le tronc est une pratique de contrôle de version où les développeurs mergent de petites mises à jour fréquentes vers un « tronc » principal ou une branche principale. C'est une pratique courante parmi les équipes DevOps et elle fait partie du cycle de vie DevOps, car elle simplifie les phases de merge et d'intégration. En fait, le développement basé sur le tronc est une pratique obligatoire pour la CI/CD. Les développeurs peuvent créer des branches éphémères avec quelques petits commits au lieu de créer des branches de fonctionnalités au long cours. Au fur et à mesure que la base de code se complexifie et que l'équipe s'élargit, le développement basé sur le tronc contribue à maintenir la fluidité des livraisons en production.

- Gitflow est un modèle de branching Git alternatif qui utilise des branches de fonctionnalité longues et plusieurs branches primaires. Comparé au développement basé sur le tronc, il dispose de davantage de branches plus longues et de commits plus importants que le développement basé sur le tronc. Dans ce modèle, les développeurs créent une branche de fonctionnalité et attendent que la fonctionnalité soit terminée pour la merger à la branche « trunk » principale. Ces branches de fonctionnalités longues nécessitent une plus grande collaboration lors du merge, car elles risquent davantage de dévier de la branche « trunk » et d'introduire des mises à jour conflictuelles.

# Sources
- https://refactoring.guru/
- https://www.atlassian.com/fr/git/tutorials
- https://www.typescriptlang.org/docs/handbook/intro.html
- https://www.paris-web.fr/2022/conferences/git-nayez-plus-peur-du-rebase.php
- https://git-scm.com/doc

# Difficulté

Pour l'instant pas de problèmes majeurs.
