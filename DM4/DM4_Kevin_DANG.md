# Connaissances

## Ce que j'ai appris :
- Différence mock, double, stub, spy, dummy, fake
- Approche inside-out et outside-in du TDD

## Ce que je connaissais déjà :
- Le Test-Driven Development
- L'injection de dépendance

# Questions
# Mise en situation n°1

- Je vais distinguer deux cas pour répondre à la situation
- Si on admet que le produit est développé avec la méthode TDD et que l'équipe de développement est à l'aise avec, réduire l'effort consacré aux tests est un non-sens.
En effet une étude de cas impliquant des équipes de Microsoft et IBM indique que le développement piloté par le temps constitue un gain de temps (environ 15-35%) et donc réduire l'effort consacré aux tests ne permet pas de sécuriser cette échéance en plus de rendre plus vulnérables au bugs et comportement imprévu, le produit.
- Dans l'hypothèse où la méthode TDD venait d'être implémenté (avec mon embauchement par exemple) et où l'équipe n'est pas encore tout à fait à l'aise avec, il est possible dans ce cas d'effectuer un compromis, en ne testant uniquement que les parties critiques et notamment les fonctionnalités que l'on souhaite montrer durant la démonstration. 
Nous mettrions alors sous le tapis certains problèmes mineurs s'ils sont découverts. Il faut alors assumer cette dette technique et s'assurer qu'elle soit rembourser après la démonstration sans faute.
- En résumé, la décision doit être prise en fonction de l'état du produit, des compétences de l'équipe de développement et de l'aspect économique de l'entreprise.

# Mise en situation n°2

- Encore une fois, deux cas de figure qui se présente.
- Si l'application dispose d'une batterie de tests complet, nous pouvons envisager une refactorisation complète de l'application, avec montée de versions.
L'existence de la batterie de test permet via la méthode TDD de s'assurer que le comportement de l'application ne change pas après la refactorisation.
- Dans le cas où l'application ne dispose pas de batterie de test, dans une situation comme cela et si la situation économique de l'entreprise le permet, il vaut mieux reprendre à partir de zéro l'application.

## Comment définissez-vous les catégories de tests suivantes ?

- tests unitaires (unit tests) : permettent de vérifier le bon fonctionnement d’une petite partie bien précise (unité ou module) d’une application.
- tests d'intégration (integration tests) : permettent de vérifier si plusieurs unités de code fonctionnent bien ensemble, dans un environnement de test.
- tests d’interface utilisateur (User Interface tests) : permettent de vérifier que tout les champs, labels, bouton et autre items sur l'écran fonctionne comme désiré.
- tests de recette (acceptance tests) : permettent de vérifier que l'application correspond aux spécifications à l'instant T.
- tests manuels (manual tests) : Un test fonctionnel est dit manuel lorsque son scénario est déroulé par un être humain. Celui-ci exploite ses 5 sens pour effectuer chaque action de la même manière que le fera un utilisateur final et contrôler que cette action entraîne bien les résultats attendus.
- tests de bout en bout (end-to-end tests) : permettent de vérifier si une application se comporte comme prévu du début à la fin. Cette technique permet de valider le fonctionnement du front. Mais aussi de vérifier son intégration avec le back-office et autres webservices.
- tests de performance (benchmarks) : permettent la validation d'une solution logicielle et de son architecture sous-jacente liées à une utilisation simultanée multi-utilisateurs, permettant ainsi d'éviter certains problèmes en production. Ils permettent de garantir une qualité de service applicative dans des conditions réelles d'utilisation.

## Décrire succinctement les patterns de tests suivants : mock, double, stub, spy, dummy, fake

- mock : `Objet` qui est une substitution complète de l’implémentation originale d’une classe concrète.
- double : `Objet` ou procédure de test qui se comporte comme des vrais, utilisés pour faciliter les tests.
- stub : Les `stubs` se substituent aux appels de méthode afin de donner des réponses pré-faites à des appels
- spy : Un `Spy` va avoir le même comportement qu’un Stub, mais il va nous permettre d’obtenir des informations supplémentaires, une fois le test effectué (comme le nombre d'appel).
- dummy : `Classe` minimal servant à satisfaire un constructeur.
- fake : Un `fake` est un objet simplifié qui sera plus facile à utiliser pour les tests. On pourrait citer l’exemple le plus courant d’une implémentation simplifiée d’une persistance d’objets.


# Le Test-Driven Development
## Est-ce une méthode de test ou une méthode de développement ? Expliquer succinctement.

- Le Test-Driven Development est une méthode de développement comme son nom l'indique. Il consiste à concevoir un logiciel par petites étapes, de façon progressive, en écrivant avant chaque partie du code source propre au logiciel les tests correspondants et en remaniant le code continuellement.
Ainsi la méthode ne décrit **comment** les tests doivent être réalisés mais **quand**.

## Quelle est la différence entre le TDD « outside-in » et le TDD « inside-out » ?
- L'approche Inside-out vise à s'assurer des dénouements précis et non de la collaboration entre les objets. C'est une pratiqque qui emploie un très faible usage de mocks pour se suffire des stubs.
Dans cette approche, qui se concentre sur la vérification de l'état d'un objet à la fois, la structure émerge au fur et à mesure.
- L'approche outside-in vise à s'assurer d'une collaboration précise entre les objets. Elle a donc tendance à promouvoir l'usage de mocks, et ainsi de démarrer depuis l'extérieur (Rest API, etc.) vers l'intérieur.
Dans cette approche, nous vérifions l'intéraction entre les objets, cela demande donc d'avoir déjà en-tête une certaine structure


# L'injection de dépendance
## A quoi ça sert l’injection de dépendance ? Quels sont les inconvénients ?
- L'injection de dépendance est un mécanisme qui permet d'implémenter le principe de l'inversion de contrôle. Il consiste à créer dynamiquement (injecter) les dépendances entre les différents objets en s'appuyant sur une description (fichier de configuration ou métadonnées) ou de manière programmatique. Ainsi les dépendances entre composants logiciels ne sont plus exprimées dans le code de manière statique mais déterminées dynamiquement à l'exécution, ce qui a pour avantage de découpler les dépendances entre objets.
- Inconvénients:
    - Augmentation de la complexité du code, généralement en augmentant le nombre de classe (séparation des responsabilité).
    - Comme pour les design pattern, la mauvaise idée serait de le marteler partout et surtout là ou il ne le faut pas. Il est possible - très courant en fait - de faire trop d’abstractions, d’ajouter trop d’indirection et d’appliquer de manière générale les bonnes techniques de manière excessive et au mauvais endroit.
    - Peut rendre les tests plus compliqués à écrire.
- En résumé, il faut du temps pour apprendre. Mal compris, cela peut causer plus de tort que de bien.
A l'extrême, cela peut représenter plus de travail que ne le justifierait l'avantage.

## Quelle est la différence entre l'injection manuelle et l'injection automatique ?
- L'injection manuelle est une injection de dépendance que nous réalisons par nous même dans le code tandis que l'injection automatique est une injection réalisé par un framework dédié. (Pas sur)
- On rappellera que l'injection de dépendance est un pattern et non un framework particulier. On peut donc l'implémenter manuellement même si c'est un exercice difficile.

## Quelle limite voyez-vous dans l’utilisation d’un framework d'injection automatique ?
- Le code sera couplé au framework d'injection de dépendance utilisé (ou plus généralement la méthode utilisé.)
- Les conteneurs DI ou les approches qui effectuent une résolution de type entraînent généralement une légère pénalité d'exécution
- Ensuite le côté magie noire, le framework est en quelque sorte une boîte noir qui résout les dépendances via divers techniques comme la reflection mais finalement on ne sait pas trop comment il fonctionne.

## Parmi les deux exemples de code suivant, lequel permet d’écrire un test sans injection de dépendance ? Quels sont les avantages et inconvénients de chacun des exemples ?

- L'exemple n°2 permet d'écrire un test sans injection de dépendance.
- L'avantage du code l'exemple 1 est un découplage de responsabilité entre le `SystemUnderTest` et sa `Dependency` qu'on peut donc remplacer facilement bien que l'inconvénient est de rendre le test plus difficile à écrire
- L'avantage du code de l'exemple 2 est une facilité de compréhension et d'écriture de test mais implique un couplage fort entre le `SystemUnderTest` et sa `Dependency`

# Sources
- https://dlinsin.blogspot.com/2009/11/dependency-injection-obscures-your-code.html
- https://ayende.com/blog/4372/rejecting-dependency-injection-inversion
- https://knplabs.com/fr/blog/mocks-fakes-stubs-dummy-et-spy-faire-la-difference
- https://apero-tech.fr/dummy-vs-fake-vs-stub-vs-mock/
- https://www.arolla.fr/blog/2020/05/test-doubles/
- https://martinfowler.com/bliki/TestDouble.html
- https://theqalead.com/general/statistics-studies-benefits-test-driven-development/#:~:text=A%20case%20study%20involving%20Microsoft,they%20used%20the%20TDD%20technique.
- https://www.microsoft.com/en-us/research/wp-content/uploads/2009/10/Realizing-Quality-Improvement-Through-Test-Driven-Development-Results-and-Experiences-of-Four-Industrial-Teams-nagappan_tdd.pdf
- https://link.springer.com/chapter/10.1007/978-3-319-91602-6_5
- https://blog.nicolas-le-borgne.fr/blog/2021/02/11/tdd-inside-out-outside-in-c-est-quoi/
- https://www.stridenyc.com/blog/outside-in-vs-inside-out-tdd
- https://blog.octo.com/un-test-peut-en-cacher-un-autre-un-peu-de-theorie/
- https://8thlight.com/insights/tdd-from-the-inside-out-or-the-outside-in
- https://victorelizalde.medium.com/tdd-inside-out-vs-outside-in-fa4aa8dac09c
- https://blog.kotlin-academy.com/dependency-injection-the-pattern-without-the-framework-33cfa9d5f312
- https://www.tests-performance.fr/?page_id=691
- https://www.guru99.com/manual-testing.html
- https://fre.myservername.com/what-is-interface-testing
- https://welovedevs.com/fr/articles/tests-unitaires/

# Difficultés
- Les mises en situations sont très intéressantes mais je pense que mes réponses sont incomplète car en effet il faut prendre en compte d'autres aspect que le côté technique quand nous sommes dans une entreprise, comme la situation économique, la valeur du produit etc.
