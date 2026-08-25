# Site web Big Budi Games

Copie de travail du site **bigbudigames.fr**, hébergé chez Infomaniak.

- **Ce dépôt** = l'atelier. On y prépare les modifications.
- **GitHub Pages** = l'aperçu. Pour voir avant de publier.
- **Infomaniak** = la vitrine. Ce que le public voit.

## La procédure, en 4 temps

1. **Demander** — décrire la modification en français courant.
2. **Modifier** — les fichiers sont édités ici et poussés sur GitHub.
3. **Regarder** — rafraîchir la page GitHub Pages, ~1 minute après.
   Rien n'est en ligne à ce stade : on peut recommencer autant de fois
   qu'il faut.
4. **Publier** — les fichiers modifiés sont envoyés dans la conversation.
   Les glisser dans le Web FTP Infomaniak par-dessus les anciens, puis
   **Ctrl+F5** sur bigbudigames.fr pour forcer l'affichage à jour.

## Où sont les fichiers

Le dépôt reproduit exactement le dossier
`/home/clients/<identifiant>/sites/bigbudigames.fr/` du Web FTP.
Un fichier ici = le même fichier là-bas, au même endroit.

```
index.html          page d'accueil
jeux.html           les jeux
catalogue.html      redirige vers jeux.html
boutique.html       redirige vers jeux.html
blog.html + blog/   le blog et ses articles
a-propos.html       à propos
contact.html        contact
sourcing.html       sourcing
style.css           toute la mise en forme du site
assets/             images et fichiers joints
robots.txt          instructions pour les moteurs de recherche
sitemap.xml         plan du site pour les moteurs de recherche
```

Chaque modification est conservée dans l'historique : on peut revenir à
n'importe quelle version antérieure du site, à tout moment.

## Comparer l'aperçu et le site en ligne

Les deux servent les mêmes fichiers. Une différence de taille à l'écran
vient du **zoom du navigateur**, que Chrome mémorise par domaine :
**Ctrl+0** sur chaque onglet remet tout à 100 %. Le contenu fait 1200 px
de large au maximum et reste centré — élargir la fenêtre n'agrandit pas
le site, ça ajoute du fond sur les côtés.

## Articles à écrire

Ces vignettes ont été retirées de la page News le 25 août 2026 : elles
annonçaient des articles qui n'existaient pas, et menaient à une page
d'erreur. Les visuels sont toujours dans `assets/blog/`. Chaque vignette
se réinstalle en quelques minutes, une fois le texte écrit.

| Article | Visuel disponible |
|---|---|
| Avignon 2026 | `assets/blog/avignon26.png` |
| Sortons Jouer 2026 (Montpellier) | `assets/blog/montpellier26.png` |
| Valence Joue 2026 | `assets/blog/valence26.png` |
| Festival JAL | `assets/blog/jal.png` |
| Festival Octogônes | `assets/blog/octogones.png` |
| 1ère visite à Vichy | `assets/blog/vichy.png` |
| Début de la communication | aucun |
| Créer Big Budi Games | aucun |

L'onglet s'appelle **News**, mais le fichier reste `blog.html` et les
articles restent dans `blog/` : renommer les fichiers casserait les liens
déjà partagés et le référencement Google.
