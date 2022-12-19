# Connaissances

## Ce que j'ai appris :
- Smart UI

## Ce que je connaissais déjà :
- Domain-Driven Design
- Différence framework et library
- Model-driven design

# Questions
## Eric Evans distingue la figure de l'expert métier, en place depuis longtemps et qui connaît parfaitement son domaine, et du développeur qui arrive pour contribuer le temps d'un projet informatique. A la fin de votre cursus, vous décidez de créer une start-up pour révolutionner un domaine d'activité (par exemple la vente en ligne). Cette distinction entre expert métier et développeur a-t-elle toujours un sens pour vous ?

- Oui cette distinction à toujours un sens pour moi. En effet, si nous prenons comme exemple la vente en ligne, je n'effectue pas un double cursus informatique et commerce. Je n'ai donc aucune connaissance dans ce secteur d'activité.
De plus, ce n'est pas parce que je souhaite révolutionner un domaine d'activité que cela signifie briser toute les règles qui ont déjà fait leurs preuves. Dans ce cas s'entourer d'experts métier pour comprendre le domaine pour ensuite le dépasser est toujours nécessaire.
Le seul cas que je vois où cette distinction serait plus ténu, c'est effectivement si l'idée de révolution tel ou tel domaine provient d'une personne possédant réellement une double compétence dans le domaine et en informatique.
Mais au final, elle jouera à la fois ce rôle d'expert métier et de développeur, de fait cette distinction est toujours existante.

## Quel vocabulaire utilisez-vous pour modéliser le domaine de la vente en ligne ?
- Le vocabulaire utilisé doit être celui du domaine métier soit de l'expert métier.
- En suivant le principe d'Ubiquitous Language, nous pouvons extraire de ce vocabulaire, un langage commun. C'est-à-dire que notre design va utiliser les termes du domaine métier. Pour la vente en ligne on se basera donc sur des termes comme :
	- Client / Acheteur
	- Produit
	- Transaction ou paiement
	- Panier
	- Commande
	- Livraison
	- Inventaire / Stock

## Quels conseils Eric Evans donne-t-il pour que votre modèle et votre design soient facilement compréhensibles ?
- Utiliser un seul langage unique basé sur le modèle et exercer l'équipe à communiquer constamment dans ce langage dans toute formes de communications qu'elle soit oral, documenté (diagrammes) ou au niveau du code.
- Jouer et expérimenter avec le modèle pour trouver des façon plus facile d'exprimer le domaine et mettre à jour le code pour être au plus près de ce model.
- Les expert métier doivent toujours vérifier si les termes ou structures utilisé sont adéquat pour la compréhension du domaine, les developpeurs doivent vérifier les ambiguités ou incohérences qui polluerai le design.
- Coupler fortement le design au modèle afin que le mapping soit évident, le design doit refléter le modèle de façon littéral pour que le code soit une expréssion du modèle à tel point qu'un changement dans le code serait un changement dans le modèle.

## Pourriez-vous me décrire le modèle et le design de votre application de vente en ligne ?
- Modèle : En reprenant le vocabulaire que nous avons définis précédemment, nous allons à présent les lier avec des règles métiers :
	- Un client souhaite acheter un ou plusieurs produits et les met dans son panier.
	- Il effectue ensuite une commande.
	- Lorsque nous recevons une commande, nous devons vérifier si les produits sont disponibles en stock
	- Si le produit est en stock, le client peut effectuer le paiement
	- Une livraison est planifiée

- Design : Le design de l'application s'appuiera sur la Layered Architecture mentionné dans Domain-Driven Design de Eric Evans ainsi que Clean Architecture de Robert C. Martin et devra donc refléter au mieux le modèle. Nous retrouverons donc du centre vers l'extérieur :
	- La couche `Domaine` qui contiendra nos `entité` comme les clients, les produits mais également des `objets-valeurs` pour représenter le stock d'un produit par exemple ainsi que nos règles métier.
	- La couche `Application` qui contiendra les cas d'utilisation de notre application
	- La couche `Infrastructure` qui gérera la persistance et l'accès au données et contiendra les façades pour des librairies externes.
	- Nous pouvons éventuellement ajouter une couche supplémentaire `Presentation` qui contiendra nos routes et controllers.
	Nous utiliserons le principe d'inversion de contrôle avec la programmation par interface et injection de dépendance afin de ne pas polluer notre domaine avec des librairies par exemple qui sont des considérations techniques.
	Ainsi chaque couche ne communiquera avec une couche plus externe externe que via une abstraction.

## Eric Evans parle de « architectural frameworks ». Quelle est la différence entre un « framework » et une « library » ?
- Un framework donne un cadre, une organisation, un squelette, une méthode de travail.
- Tandis que la librairie, elle, n'offre que des fonctionnalités souvent décorrélées les unes des autres.
- Le développeur utilise une bibliothèque en appelant le code de cette dernière, tandis que le rôle du framework est d’exécuter le code du développeur.

## Dans quel secteur d'activité vous voyez-vous dans les 3 ans qui viennent ? Dans ce secteur, savez-vous laquelle des approches suivantes est la plus répandue : Smart UI ou Model-Driven Design ? En entretien d'embauche, comment pourriez-vous savoir si l'équipe pour laquelle vous postulez applique efficacement l'approche Domain-Driven Design ?
- Je vais me permettre de tricher un peu et partir du principe que je souhaite rester dans mon entreprise actuel au moins pour les 3 années à venir. Cette entreprise travaille donc dans le domaine de la vidéo et propose un logiciel de montage vidéo simple à base de template.
Ce qui est intéressant pour la question est qu'effectivement comme dans beaucoup d'entreprise, nous pouvons considérer que plusieurs applications fonctionne ensemble pour former le produit total (Front, Back, Back Office, ect...), et je travaille donc sur plusieurs applications.
Dans les faits, pour notre front (et les applications de type front en général je pense), l'approche Smart UI est sans doute la plus répandue pour les avantages énoncé dans le livre comme une grande productivité pour les applications simples, ce qui est le cas d'un front.
Mais si j'en reviens à mon domaine métier qui donc la vidéo, si on entre un peu plus dans le domaine, on comprendra que le coeur du notre métier est la génération de vidéo (à partir de template). 
Ainsi le générateur de vidéo est une autre application à part et l'approche utilisé est donc le Model-driven design, car en effet le code, en plus de suivre la Layered Architecture, est le résultat d'un modèle basé sur tout les discussions en amont avec les expert métier de la vidéo (les motions designers), notamment les créateurs de template justement.

- En entretien d'embauche, pour savoir si l'équipe pour laquelle je postule applique efficacement le DDD, je demanderai si les développeurs échangent régulièrement avec les experts métiers afin de peaufiner le modèle, si un langage commun a été mis en place pour communiquer entre développeurs et experts métier et enfin je poserai des questions sur l'architecture de l'application (Architecture en couche, Clean architecture, Onion architecture, Hexagonal Architecture), le but étant de savoir le métier est représenté directement dans le code.

# Edit suite au cours (seul le domaine change pour aller de la vente en ligne vers l'assurance et pour uniquement deux question)
## Quel vocabulaire utilisez-vous pour modéliser le domaine des assurances ?
- Le vocabulaire utilisé doit être celui du domaine métier soit de l'expert métier.
- En suivant le principe d'Ubiquitous Language, nous pouvons extraire de ce vocabulaire, un langage commun. C'est-à-dire que notre design va utiliser les termes du domaine métier. Pour l'assurance on se basera donc sur des termes comme :
	- Client
	- Devis
	- Contrat
	- Remboursement
	- Sinistre
	- Souscription
	- Paiement

## Pourriez-vous me décrire le modèle et le design de votre application d'assurance ?
- Modèle : En reprenant le vocabulaire que nous avons définis précédemment, nous allons à présent les lier avec des règles métiers :
	- Un client souhaite obtenir un devis afin de souscrire à une assurance.
	- Si le devis lui convient, il effectue un paiement pour souscrire à l'assurance et obtient un contrat.
	- Le client souhaite être remboursé en cas de sinistre

- Design : Ne change pas par rapport à l'application de vente en ligne donc je ne détaillerai pas ici.


# Sources
- Domain-Driven Design, Eric Evans

# Difficultés
- La modélisation est certainement difficile justement car je ne suis pas un expert métier de la vente en ligne.
