# Score Keeper — Plan de développement

Feuille de route vers la parité fonctionnelle avec les meilleures apps de pointage de l'App Store iOS.
Dernière mise à jour : 2026-07-13.

## Apps analysées (App Store, juillet 2026)

| App | Note | Points forts |
|---|---|---|
| [Point Counter - Scoreboard](https://apps.apple.com/ca/app/point-counter-scoreboard/id6448441700) | 4,7 ⭐ (132) | Tableaux multiples, interface épurée |
| [Scoreboard: Score Keeper](https://apps.apple.com/ca/app/scoreboard-score-keeper/id6739888813) | 4,5 ⭐ | Classement en direct, stats et historique, minuterie, duplication de partie |
| [Score Keeper Point Counter](https://apps.apple.com/ca/app/score-keeper-point-counter/id6468240268) | 4,5 ⭐ (52) | Tableaux multiples nommés, équipes, gros caractères |
| [Counter +](https://apps.apple.com/ca/app/counter/id478557426) | 4,4 ⭐ (17) | Journal d'activité, rapports exportables, mode gaucher, sons/vibration |
| [Tally: Counter & Score Tracker](https://apps.apple.com/ca/app/tally-counter-score-tracker/id1412716242) | 4,3 ⭐ (61) | Widgets iOS, Siri, iCloud, export CSV (abonnement payant) |

## Déjà à parité (ou mieux)

- [x] Joueurs multiples avec nom (30 car.) et couleur
- [x] Incréments configurables (bonds prédéfinis + personnalisé global + montant par joueur)
- [x] Score pour gagner configurable + **animation de victoire** (aucun concurrent ne l'a)
- [x] Thème clair/sombre + 4 styles visuels (Sobre, Moderne, Années 80, Mono)
- [x] Multilingue FR / EN / IT / ES
- [x] Nom et type de jeu (cartes, plateau, dés, autre) avec icônes adaptées
- [x] App web installable sur l'écran d'accueil avec icône (PWA)
- [x] Gratuit, sans pub, sans abonnement (Tally et Scoreboard font payer leurs fonctions avancées)

## Phase 1 — Indispensables (fait)

- [x] **Persistance de la partie** : joueurs et scores sauvegardés (`localStorage`), la partie survit au rechargement et à la fermeture de l'app
- [x] **Annuler (undo)** : reprendre les dernières actions (points, ajout/retrait de joueur, remises à zéro), pile de 50 actions

## Phase 2 — Cœur de la parité (fait)

- [x] **Classement en direct** : indicateur de position (1er, 2e…) ou tri optionnel des joueurs par score
- [x] **Parties multiples** : sauvegarder plusieurs tableaux nommés, reprendre une partie, dupliquer une partie (mêmes joueurs et règles)
- [x] **Profils de joueurs réutilisables** d'une partie à l'autre

## Phase 3 — Confort et différenciation (fait)

- [x] **Historique des points** : journal des changements (qui, combien, quand) consultable par partie
- [x] **Statistiques** : parties jouées, victoires par joueur, moyennes
- [x] **Minuterie de tour** intégrée
- [x] **Plus de 6 joueurs** : limite portée à 12 (mode équipes non retenu pour l'instant)
- [x] **Export / partage** : résultats en CSV ou image à partager
- [x] **Sons et vibration** au toucher (option dans les paramètres; haptique limitée sur iOS web)

## Hors de portée (web app vs native)

Réservé aux apps natives iOS, impossible en PWA :

- Widgets d'écran d'accueil et d'écran verrouillé
- Raccourcis Siri
- Synchronisation iCloud entre appareils (alternative possible : export/import manuel d'un fichier de sauvegarde)

## Notes techniques

- Une seule page `index.html` auto-suffisante (CSS + JS inline), hébergée sur GitHub Pages : https://jifbrodeur.github.io/Pointage/
- Réglages persistés dans `localStorage` : thème (`cc-theme`), style (`cc-skin`), langue (`cc-lang`), bond par défaut (`cc-step`), nom du jeu (`cc-game`), type de jeu (`cc-type`), points pour gagner (`cc-goal`), parties et joueurs (`cc-games`, `cc-current`)
