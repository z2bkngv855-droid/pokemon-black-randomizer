# Pokémon Black Randomizer

Interface publique mobile-first pour préparer une randomisation de Pokémon Noir (Gen V).

## État du projet

Cette première publication est une interface et un point d'entrée. Elle **n'embarque pas encore le moteur de modification des ROM**. Ne sélectionnez pas une ROM en pensant qu'elle sera transformée par cette page.

Le moteur de randomisation doit être intégré et testé sur la ROM française Pokémon Noir (IRBF) avant de proposer un téléchargement généré.

## Objectif fonctionnel

- Pokémon Noir / Blanc (génération V)
- Starters, rencontres sauvages, Pokémon statiques, équipes de dresseurs et légendaires
- Talents, statistiques, types et évolutions
- Attaques : capacités apprises par niveau, puissance, précision, PP, type et catégorie physique/spéciale ; attaques des équipes de dresseurs et compatibilité TM/tutoriels selon les options du moteur
- EV/IV : traitement spécifique à valider, car ce n'est pas une option standard du moteur UPR-ZX
- ROM fournie par l'utilisateur, jamais incluse dans le dépôt

## Confidentialité

La page actuelle ne reçoit ni n'envoie de ROM. La future intégration devra privilégier un traitement local dans le navigateur et ne jamais publier de ROM sur GitHub.

## Licence

Le projet Universal Pokémon Randomizer ZX est sous GPL-3.0-or-later. Toute intégration de son code devra conserver les notices et obligations de licence applicables. Pokémon et les marques associées appartiennent à leurs ayants droit.


## Publication
Le déploiement GitHub Pages est configuré via GitHub Actions.

## Critères de validation avant annonce « prêt »

- [ ] Le moteur tourne dans le navigateur mobile et traite la ROM localement.
- [ ] Pokémon Noir français identifié par son empreinte/version (IRBF) ; aucune compatibilité ne sera annoncée avant test réel.
- [ ] Les attaques apprises par niveau et les paramètres des attaques sont randomisés selon les options sélectionnées.
- [ ] Les attaques indispensables à la progression (notamment capacités de terrain / scripts) sont protégées ou remplacées de façon sûre.
- [ ] Starters, rencontres, Pokémon statiques, équipes de dresseurs, talents, stats, types, évolutions et objets passent des tests de non-corruption.
- [ ] Le fichier `.nds` généré se télécharge, s'ouvre dans un émulateur DS et passe un test de démarrage / sauvegarde.
- [ ] Les EV/IV sont soit réellement intégrés et testés, soit clairement signalés comme non pris en charge ; aucune promesse fictive.
- [ ] Aucune ROM utilisateur n'est envoyée au serveur ou commitée dans GitHub.
