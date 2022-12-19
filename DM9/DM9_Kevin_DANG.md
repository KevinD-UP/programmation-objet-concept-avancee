# Connaissances

## Ce que j'ai appris :
- Différence plus claire entre continous delivery et continuous deployment
- Environnement de qualification/recette/performance/staging/démonstration
- Cycle en V en détail

## Ce que je connaissais déjà :
- Environnement développement/préproduction/production
- L'approche DevOps
- CI/CD
- SemVer
- Différence Machine Virtuel et Conteneur.

# Questions
## Qu’est-ce que l’approche « DevOps » ? Quels problèmes cette approche cherche-t-elle à résoudre ?

- L'approche DevOps est une méthodologie de meilleures pratiques informatiques qui réunit les développeurs et l'équipe chargée des opérations afin de développer et de distribuer rapidement de nouveaux services et de nouvelles fonctionnalités logicielles. L'approche DevOps permet aux équipes de collaborer et d'accélérer le processus entre le développement et le déploiement, tout en continuant d'améliorer les points suivants :
	- Qualité
	- Sécurité
	- Fiabilité

## Qu’appelle-t-on l’intégration continue (continuous integration) ? Le continuous delivery ? Le déploiement continu (continuous deployment) ?
- L'intégration continue désigne un processus d'automatisation pour les développeurs. Si les développeurs parviennent à apporter régulièrement des modifications au code de leur application, à les tester, puis à les fusionner dans un référentiel partagé, cela signifie que l'intégration continue est réussie. Cette solution permet d'éviter de travailler en même temps sur un trop grand nombre d'éléments d'une application, qui pourraient entrer en conflit les uns avec les autres.
- Le continuous delivery automatise la publication du code validé dans un référentiel. Aussi, pour garantir l'efficacité du processus de distribution continue, il faut d'abord introduire le processus d'intégration continue dans le pipeline de développement. La distribution continue permet de disposer d'un code base toujours prêt à être déployé dans un environnement de production.
- L'étape finale d'un pipeline CI/CD mature est le déploiement continu. En complément du processus de distribution continue, qui automatise la publication d'une version prête pour la production dans un référentiel de code, le déploiement continu automatise le lancement d'une application dans un environnement de production. En l'absence de passerelle manuelle entre la production et l'étape précédente du pipeline, le déploiement continu dépend surtout de la conception de l'automatisation des processus de test.

## Décrire les usages des environnements suivants :
- démonstration : Environnement dédié à la démonstration client.

- développement : On commence ainsi à déployer chaque livrable sur l’environnement de développement et on le soumet à une première phase de tests. Le premier de ces tests consiste à valider la mécanique de déploiement. C’est en effet la première fois qu’on tente de déployer ce livrable quelque part. Le bon déroulement du déploiement constitue une première étape pour se rassurer sur notre capacité à livrer le produit jusqu’en production.
On va ensuite valider sur cet environnement un certain nombre de propriétés de notre système (fonctionnelles ou non fonctionnelles) mais aussi la validité de certaines configurations de notre livrable.
Si tout est ok, on peut alors promouvoir le livrable et le déployer sur l’environnement suivant pour la phase d’intégration.

- intégration : Dans cette phase, le système validé isolément est mis en présence des autres systèmes de la solution logicielle. Il pourra alors être mis en jeu dans la phase de tests d’intégration de systèmes qui vise à dérouler des usecases métier qui traversent plusieurs systèmes afin de valider le bon branchement des différents éléments de la solution.
A chaque succès de la validation sur l’environnement de développement, on peut mettre à jour cet environnement d’intégration.

- performance : Environnement dédié au tests de performance.

- préproduction :
En préproduction, on procède à une dernière phase de tests avant de mettre en production, en déployant uniquement les fonctionnalités qu’on décide de mettre en production lors de la prochaine release. Cette décision n’est pas une étape nécessaire et elle est souvent liée à une décision marketing ou commerciale.
Il s’agit bien souvent sur cet environnement d’opérations de recette et d’acceptation, qui n’ont pas vocation à détecter des bugs dans le produit. Si des bugs sont trouvés à cette étape, c’est bien souvent signe d’un manque de test dans une des étapes précédentes.
Si la livraison en production n’est pas liée à des contraintes de communication client ou d’accompagnement de ces derniers, on peut tout à fait envisager de n’avoir qu’un seul environnement « pré-production », en lieu et place des environnements d’intégration et de préproduction. On accepte alors la contrainte (ou l’avantage) que tout le code validé en dev part tout droit en production s’il passe avec succès les étapes de validation suivantes.

- production : L'environnement de production héberge les applications utilisées par les utilisateurs. Certains tests d’un type différent peuvent tout à fait se dérouler en production, on parle souvent de « Tests Post Déploiement ». Il s’agit là plutôt de valider les aspects liés à l’environnement, les configurations spécifiques, les systèmes de monitoring ou encore de ce que je qualifierais d’expérimentations fonctionnelles (canari testing, A/B testing, feature flipping) etc…
A cette étape, l’objectif n’est pas non plus de détecter d’éventuels bugs dans un des systèmes mis en jeu (même si cela peut arriver !)

- qualification : Cette environnement vise à effectuer des tests permettant de,vérifier la conformité de l’ensemble du logiciel par rapport aux exigences. (plus communément appelé recette.)

- recette : L'environnement de recette est utilisé pour validation des production auprès des recetteurs (utillisateurs tests) avant mise en production.
Cet environnement permet de valider le processus de déploiement et de configuration (à partir du repository applicatif et du gestionnaire de configuration).

- staging : Le staging permet de valider une correction à apporter rapidement en production. On déploiera sur cet environnement le code actuel de production, avec pour seule modification la correction apportée, en vue de valider la bonne correction du problème constaté. On vérifie également l’absence d’effet de bord (régressions) de cette modification apportée au produit.

## Comment ces environnements sont-ils utilisés en cycle en V et en méthode agile ? Quel est l’ordre de déploiement d’une nouvelle version dans chacun de ces environnements ? Tous ces environnements sont-ils toujours utilisés ?
- En cycle en V, nous avons les phases de tests unitaires, d'intégration, de tests fonctionnels et enfin test d'acceptation (recette). Nous déploirons donc chaque nouvelle version dans l'ordre suivant : développement -> intégration -> préproduction/recette/qualification -> production
- En méthode agile, nous avons un ordre similaire développement -> intégration -> préproduction -> production, mais ce processus se caractérise par une automatisation de la livraison d’un produit logiciel qui a pour vocation à être systématique et répétitive.
- Tout ces environnements ne sont pas toujours utilisés, et leurs rôles peuvent parfois se confondre.

## Pour chaque type de tests vu dans le DM 4, déterminer quel est l’environnement dans lequel ces tests sont exécutés.

| Type de tests 	            | Environnement |
| -----------    	            | -----------   |
| tests unitaires               | développement |
| tests d'intégration           | intégration   |
| tests d’interface utilisateur | tous          |
| tests de recette              | recette       |
| tests manuels                 | tous          |
| tests de bout en bout         | préproduction |
| tests de performance          | performance   |

Note : J'ai personnellement énormément de mal avec cette question. En effet, la procédure pour moi au sein d'une pipeline serait de lancer tout les tests automatiques (unitaire/intégration/end-to-end) avant de déployer dans un environnement. Au final, il ne resterait alors que des tests manuels ou de recette à faire sur l'environnement où l'application est déployé. Je pense que cette difficulté vient du fait que beaucoup d'environnement se confondent par exemple qualification et recette.

## Qu’est-ce que le SemVer ? Illustrer par un exemple pour chaque type : majeur, mineur ou patch.
- SemVer (voulant dire Semantic Versioning) est une gestion sémantique des versions. En d'autres termes, une façon de numéroter les versions de manière logique, cohérente, parlante, ayant du sens.
- Selon la spécification de la gestion sémantique de version est écrite par Tom Preston-Werner, inventeur de Gravatars et cofondateur de GitHub :
Étant donné un numéro de version MAJEUR.MINEUR.CORRECTIF, il faut incrémenter :

le numéro de version MAJEUR quand il y a des changements non rétrocompatibles,
le numéro de version MINEUR quand il y a des ajouts de fonctionnalités rétrocompatibles,
le numéro de version de CORRECTIF quand il y a des corrections d’anomalies rétrocompatibles.
Des libellés supplémentaires peuvent être ajoutés pour les versions de pré-livraison et pour des méta-données de construction sous forme d’extension du format MAJEURE.MINEURE.CORRECTIF.
- Majeur : 1.0.0 -> 2.0.0
- Mineur : 1.10.0 -> 1.11.0
- Patch : 1.0.0 -> 1.0.1

## Quelles sont les différences les plus importantes entre les solutions d’isolation logicielle suivantes :
- Machines virtuelles (KVM, Qemu, Xen, VMWare) : Une machine virtuelle ou VM est un environnement entièrement virtualisé qui fonctionne sur une machine physique. Elle exécute son propre système d’exploitation (OS) et bénéficie des mêmes équipement qu’une machine physique : CPU, mémoire RAM, disque dur et carte réseau. Plusieurs machines virtuelles avec des OS différents peuvent coexister sur le même serveur physique : Linux, MacOS, Windows…
- Docker est un outil qui utilise des conteneurs pour faciliter la création, le déploiement et l'exécution d'une application. Il lie l'application et ses dépendances à l'intérieur d'un conteneur.
- LXC, contraction de l’anglais Linux Containers est un système de virtualisation, utilisant l'isolation comme méthode de cloisonnement au niveau du système d'exploitation. Il est utilisé pour faire fonctionner des environnements Linux isolés les uns des autres dans des conteneurs, partageant le même noyau et une plus ou moins grande partie du système hôte.
- JVM, contraction de Java Virtual Machine est un environnement d'exécution pour applications Java.
C'est un des éléments les plus importants de la plate-forme Java. Elle assure l'indépendance du matériel et du système d'exploitation lors de l'exécution des applications Java. Une application Java ne s'exécute pas directement dans le système d'exploitation mais dans une machine virtuelle qui s'exécute dans le système d'exploitation et propose une couche d'abstraction entre l'application Java et ce système.
- Python virtualenv : virtualenv est un outil pour créer des environnements virtuels Python isolés. virtualenv crée un dossier qui contient tous les exécutables nécessaires pour utiliser les paquets qu’un projet Python pourrait nécessiter.
- Instance AWS : Une instance EC2 est un serveur virtuel hébergé dans Elastic Compute Cloud (EC2) pour exécuter des applications sur l'infrastructure Amazon Web Services (AWS)
- Serveur dédié : Un serveur dédié est un type de serveur informatique ayant pour particularité de proposer ses services à un seul et unique client. Il s'oppose, par définition, au serveur mutualisé qui apporte, de son côté, une réponse aux requêtes de plusieurs utilisateurs simultanément.

# Sources
- https://www.padok.fr/blog/devops-tout-savoir
- https://www.juniper.net/fr/fr/research-topics/what-is-devops.html
- https://www.redhat.com/fr/topics/devops
- https://www.syloe.com/glossaire/approche-devops/
- https://www.redhat.com/fr/topics/devops/what-is-ci-cd
- https://www.arcadsoftware.fr/solutions-fr/ci-cd-integration-continue-deploiement-continu/
- https://www.oracle.com/fr/cloud/definition-approche-ci-cd/
- https://semver.org/lang/fr/
- https://putaindecode.io/articles/semver-c-est-quoi/#:~:text=Pour%20faire%20simple%2C%20SemVer%20(voulant,%2C%20parlante%2C%20ayant%20du%20sens.
- https://blog.atinternet.com/fr/integration-continue-le-code-les-livrables-et-les-environnements/
- https://www.oracle.com/fr/cloud/definition-machine-virtuelle-vm/
- https://datascientest.com/docker-guide-complet
- https://aws.amazon.com/fr/docker/
- https://www.redhat.com/fr/topics/containers/what-is-docker
- https://geekflare.com/fr/docker-vs-virtual-machine/
- https://fr.wikipedia.org/wiki/Cycle_en_V

# Difficultés

- Les tests et les environnements qui peuvent être confondus ou ayant des rôles similaires
