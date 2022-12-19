# Connaissances

## Ce que j'ai appris :
- Le Joel Test
- Les pratiques de Alan, Valve et Medium
- Engineering Growth Framework
- Différence licenciement, une rupture conventionnelle et une démission
- Twelve-Factor App

## Ce que je connaissais déjà :
- Conventions collectives

# Questions
## Sur l’application à développer en groupe, quelle note vous donnez-vous au « Joel Test » ? Ce test a maintenant 20 ans, voyez-vous des questions qui ont perdues de leur pertinence ?
- Utilisez-vous un système de gestion de version ? 1
- Pouvez-vous effectuer une compilation en une seule étape ? 1
- Faites-vous des compilations journalières ? 1
- Avez-vous un logiciel de suivi de problèmes ? 1
- Corrigez-vous les bugs avant d'écrire de nouvelles fonctionnalités ? 1
- Avez-vous un planning de développement à jour ? 1
- Avez-vous des spécifications fonctionnelles ? 1
- Les programmeurs ont-ils un environnement de travail calme (facilités à la concentration, etc.) ? 1
- Utilisez-vous les meilleurs outils que vous puissiez vous payer ? 1
- Avez-vous des testeurs ? 0
- Les candidats doivent-ils écrire du code pendant leur entretien d'embauche ? 0
- Faites-vous des tests utilisateur complet ? 0

- Note final : 9/12
- Je ne vois pas de questions ayant perdues de leur pertinence malgré ces 20 années. Mais elles peuvent avoir prises des formes plus moderne, par exemple les compilations journalières peuvent être assimiler à l'intégration continue.

## Si vous êtes recruté chez Alan après votre master, quelle salaire pouvez-vous prétendre ? Et combien de stock-options ? Si vous restez 5 ans et progressez au niveau E, quel sera alors votre salaire ?
- Difficile de répondre à la première question, car le salaire dépend du niveau et le niveau est évalué durant les entretiens. En partant du principe de prendre le niveau le plus bas et s'il ne compte pas mes années d'alternance, je devrais être au niveau C0 et prétendre à un salaire de 52K selon leur grille de salaire.
- Je pourrai donc prétendre à 1500 stock-option
- Si je reste 5 ans et que je progresse au niveau E, le salaire est de 80K

##  Toujours chez Alan, sur quels critères est évaluée votre progression ? Des 5 axes pris en compte, sur lequel êtes vous le plus confiant ? Le moins confiant ?
- La progression est évaluer sur des critères techniques, de collaborations, de recrutements, de portées et de mentorats
- Je suis le plus confiant sur le critère technique.
- N'ayant jamais effectuer de processus de recrutement en tant que recruteur, je suis donc moins confiant dans le critère recrutement.

## Vous souhaitez être recruté chez Valve. Avant de passer des entretiens, comment pourriez-vous trouver des informations sur les sujets suivants ? Le processus d’onboarding ? le management et la structure hiérarchique ? L’évaluation et la politique salariale

- Ces informations sont facilement trouvable sur internet. En effet, ils existent par exemple en ligne, le guide pour les nouveaux employés (dans plusieurs langues) :
https://cdn.cloudflare.steamstatic.com/apps/valve/Valve_NewEmployeeHandbook.pdf qui donne énormément d'information sur les processus d'onboarding ainsi que les méthodes de management et la structure hiérarchique

- Nous pouvons également trouver des témoignages d'anciens employés afin de se faire une idée sur l'évaluation et la politique salariale.

## Quelles pratiques sont mises en œuvre chez Medium afin de développer les compétences des employés ? (10 lignes max)
- Medium utilise ce qu'ils appellent le Engineering Growth Framework. Ils donc mis en place 16 disciplines regroupés dans 4 catégories qui constituent des pistes pour se développer et progresser.
- Ces 4 catégories sont Building, Executing, Supporting, Strenghtening.
- Les 16 disciplines sont Mobile, Web Client, Foundations, Servers Project Management, Communication, Craft, Initiative Career Development, Org Design, Wellbeing, Accomplishment, Mentorship, Evangelism, Recruiting, Community
- Chacune des catégories possèdent des indicateurs qui donne un indice sur les qualités requises pour progresser même si elles sont plutôt à but informatives que prescriptives.

## Quelle sera votre convention d’entreprise si vous travaillez dans une ESN ? Quelles sont les différences les plus importantes que vous voyez entre cette convention et la convention Bancaire ?
La convention d'entreprise dans une ESN est la convention Syntec.

## Quelle la différence entre un licenciement, une rupture conventionnelle et une démission ?
- Le licenciement est la mesure par laquelle, agissant d'une manière unilatérale, un employeur met fin au contrat de travail qui le lie à un salarié.
- La rupture conventionnelle quant à elle doit nécessairement découler d'une volonté commune de mettre fin au contrat de travail. L'employeur et le salarié doivent s mettre d'accord sur les conditions de rupture du contrat en signant une convention de rupture conventionnelle.
- La démission découle de la seule initiative de l'employé. L'employeur n'intervient pas dans votre choix, il ne doit pas vous pousser à démissionner. Démissionner doit résulter de votre propre volonté claire et non équivoque.

# Ops avancé (partie facultative)
## Dans quels contextes la méthode « Twelve-Factor App » est-elle appropriée ?
- La méthode « Twelve-Factor App » est appropriée dans le développement de systèmes complexe necessitant beaucoup de dépendance ou un hebergement sur le cloud par exemple.

## Quelles pratiques de la méthode « Twelve-Factor App » ne vous sont pas familières ?
- Je ne connaissais pas le nom de la méthode mais chacune de ces 12 pratiques me sont familières.

## Vous souhaitez ajouter du monitoring sur votre application. La stack vous est imposée : Cloudwatch + prometheus + grafana. Décrire succinctement le rôle de ces trois briques. Comment intégrer ces trois briques ensembles ? Quelles solutions choisiriez-vous pour héberger la stack de monitoring ?
- Cloudwatch contient les logs de l'application, Prometheus est le collecteur de metric de l'application et enfin Grafana est une plateforme permettant d'afficher de façon lisible pour un humain ces metric sous formes de graphes par exemple.
- Une infrastructure AWS pourrait-être mis en place pour héberger la stack de monitoring.

## (Si vous avez vraiment beaucoup de temps) Mettre en place le monitoring sur votre application.

# Sources
- https://fr.wikipedia.org/wiki/Test_de_Jo%C3%ABl
- https://www.joelonsoftware.com/2000/08/09/the-joel-test-12-steps-to-better-code/
- http://codeur-pro.fr/le-test-de-joel/
- https://medium.com/s/engineering-growth-framework
- https://medium.com/s/engineering-growth-framework/engineering-growth-introduction-8ba7b78c8d6c
- https://medium.com/s/engineering-growth-framework/engineering-growth-appeals-process-25a2161ed582
- https://medium.com/s/engineering-growth-framework/engineering-growth-assessing-progress-743620e70763
- https://medium.com/s/engineering-growth-framework/engineering-growth-tracks-b1fad620787e
- https://medium.com/s/engineering-growth-framework/engineering-growth-framework-overview-4e02ab330524
- https://blog.alan.com/bien-etre-au-travail/au-clair-sur-les-salaires
- https://medium.com/alan/engineering-career-path-at-alan-e5de5c2e740c
- https://www.valvesoftware.com/en/publications
- https://cdn.cloudflare.steamstatic.com/apps/valve/Valve_NewEmployeeHandbook.pdf
- https://www.juritravail.com/Actualite/demission-ou-rupture-conventionnelle-le-grand-comparatif/Id/8856#:~:text=La%20d%C3%A9mission%20n'ouvre%20pas,indemnit%C3%A9%20compensatrice%20de%20cong%C3%A9s%20pay%C3%A9s.
- https://www.journaldunet.fr/management/guide-du-management/1131545-salaire-minimum-dans-les-esn-ce-qu-impose-la-convention-syntec/
- https://www.dictionnaire-juridique.com/definition/licenciement.php
- https://medium.com/@quentin.farizon/startup-web-app-12-factors-45c54eef0665

# Difficultés
