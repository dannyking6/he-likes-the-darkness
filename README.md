# He Likes The Darkness — build hors-ligne

Jeu de puzzle/platformer : guide un petit personnage qui **n'a peur que de la lumière**.
Cache-toi dans l'ombre, évite les faisceaux, atteins la sortie. 71 niveaux, 7 mondes.

- **Concept original** : inverse les codes du platformer (la lumière = danger, l'obscurité = safe).
- **Moteur** : Construct 3 (export web).
- **Portail d'origine** : GameSnacks — version ici **100 % autonome, sans SDK, sans ads, sans réseau**.

## Lancer le jeu

Il faut un petit serveur HTTP local (pas d'installation, rien à télécharger) :

```bash
cd he-likes-the-darkness
python3 -m http.server 8080
# puis ouvrir http://localhost:8080 dans le navigateur
```

Tout est servi depuis ce dossier : aucune requête internet n'est faite.

## Contrôles

- **Tactile** : boutons virtuels en bas de l'écran (gauche / droite / saut).
- **Souris** : cliquer les menus ; le jeu est en paysage (landscape).

## Ce qui a été retiré / modifié

- SDK GameSnacks + wrapper Google h5games remplacés par un driver neutre local (`game-driver.js`)
  qui implémente la même surface API (ads factices instantanées, storage localStorage, audio, score).
- Suppression : appels réseau, analytics, chargement différé externe, service worker distant.
- Aucun sitelock n'était présent ; aucun fichier de jeu (logique, assets) n'a été altéré.

## Validation (Playwright + firewall applicatif)

- 0 erreur JS, 0 requête échouée, **0 requête externe** (firewall).
- Boucle de rendu active (~120 fps), navigation complète intro → tuto → mondes → niveau.
- Preuve gameplay : le personnage saute physiquement via les contrôles tactiles (position y 549 → 459 lue dans le runtime).
