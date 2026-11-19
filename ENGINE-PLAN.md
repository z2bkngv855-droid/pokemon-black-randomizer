# Moteur de randomisation — décision technique

## Besoin produit

Le site doit permettre à l'utilisateur de sélectionner sa propre ROM Pokémon Noir française (référence signalée : IRBF), de choisir les catégories à randomiser, puis de télécharger un fichier NDS généré sur son appareil mobile. La ROM ne doit jamais être téléversée sur un serveur ni ajoutée au dépôt.

## Piste prioritaire à évaluer

Le candidat le plus proche du besoin observé est le moteur Universal Pokémon Randomizer ZX 4.6.1 adapté au navigateur avec TeaVM, utilisé par PokéRuns. La page publique annonce 122 réglages pour les générations I à V et présente notamment les options suivantes pour les attaques :

- attaques apprises par niveau / learnsets ;
- puissance, précision, PP et type des attaques ;
- catégorie physique / spéciale ;
- meilleures attaques dans les movesets et protection de certaines attaques problématiques ;
- attaques des équipes de dresseurs ;
- CT, CS, tuteurs et compatibilité associée.

La page annonce aussi la prise en charge des jeux officiels des générations I à V, mais précise que les autres éditions que sa ROM allemande de test n'ont pas toutes été vérifiées. Cela ne prouve donc pas la compatibilité de la ROM française IRBF.

Références à examiner avant intégration :
- https://randomizer.pokeruns.com/
- https://github.com/Ajarmar/universal-pokemon-randomizer-zx
- https://github.com/justinelijahtaylor/randomize.sh (port TypeScript mobile, mais son README indique que Gen V n'est pas encore branchée dans l'interface web).

## Architecture cible

1. Interface statique mobile-first servie gratuitement par GitHub Pages.
2. Lecture de la ROM via le navigateur (File API), sans upload.
3. Moteur exécuté localement, idéalement dans un Web Worker pour ne pas bloquer l'interface.
4. Contrôle d'intégrité avant et après transformation.
5. Téléchargement local du fichier NDS et d'un journal de seed/options.
6. Gestion claire des erreurs : ROM inconnue, édition/langue non prise en charge, mémoire insuffisante, randomisation interrompue.

## Points de compatibilité à résoudre

- Identifier la ROM IRBF par taille, en-tête et empreinte cryptographique, sans supposer que le code régional suffit.
- Vérifier les tables de textes et les offsets de la version française ; les moteurs UPR ciblent historiquement surtout les ROM anglaises.
- Tester les attaques apprises, attaques des dresseurs, CT/CS et tuteurs séparément.
- Préserver les capacités nécessaires aux scripts et à la progression (ex. CS / attaques de terrain) ou fournir un remplacement cohérent.
- Tester le démarrage, les combats, les sauvegardes et les transitions de zones dans un émulateur DS.
- Évaluer EV/IV séparément : ne pas promettre cette fonction tant qu'un traitement spécifique n'est pas implémenté et testé.

## Licence et distribution

Le moteur UPR-ZX est annoncé sous GPL-3.0-or-later. Toute réutilisation ou modification doit conserver les notices, fournir les sources correspondantes et respecter les obligations GPL applicables. Aucun fichier ROM, dump propriétaire ou asset non autorisé ne doit être ajouté au dépôt.

## Critère de sortie

Ne marquer le site « prêt » qu'après une génération complète et reproductible depuis un navigateur mobile, avec test de la ROM française cible et vérification d'un NDS généré dans un émulateur. Une page publiée ou une interface qui ne transforme pas réellement la ROM ne constitue pas une version prête.
