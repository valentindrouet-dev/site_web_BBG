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

## Le cache du navigateur — à savoir avant de publier

Les pages portent `style.css?v=AAAAMMJJNN` (date + numéro du jour). Ce suffixe n'a qu'un rôle :
quand la feuille de style change, le numéro change aussi, l'adresse n'est
plus la même et les navigateurs vont chercher la nouvelle version au lieu
de ressortir celle qu'ils gardaient en mémoire.

**Sans lui**, un visiteur déjà venu voit les nouvelles pages avec
l'ancienne mise en forme : images à leur taille d'origine, mise en page
disloquée. C'est arrivé le 9 octobre 2026.

À chaque modification de `style.css`, le numéro doit être relevé dans
toutes les pages (onze à ce jour, fiches de jeux comprises). Sinon, le symptôme revient — et Ctrl+F5 ne soigne que le
poste depuis lequel on regarde, pas celui des visiteurs.

## La charte graphique dans la feuille de style

Toutes les couleurs sont des variables en tête de `style.css`, nommées comme
dans la charte d'AMMA Studio (`--jaune`, `--creme`, `--brun`, `--orange`…).
Pour changer une teinte partout, c'est là, et seulement là.

Les formes « posées à la main » (bandeau des boutons, cadres décalés) sont
des découpes CSS, pas des images : elles se recolorent librement.
Le dossier `assets/charte/` contient les pictogrammes tirés de la charte
(banane et pièce, bulle à chiffre, flèche, contours blancs) et la tuile du
motif de fond.

Sur téléphone, tout le site est affiché à 90 % (réglage unique `--zoom-mobile`,
en fin de `style.css`) : un rendu un peu « dézoomé », préféré au 100 %. Les champs
de saisie et le bouton menu gardent leur taille réelle à l'écran (16 px et 44 px).

Polices : Lilita One pour tout ce qui est en capitales, Baloo 2 pour le texte.
Servies par le site depuis `assets/fonts/`, sans appel à Google.
Elles sont préchargées en tête de chaque page et réglées pour ne jamais
afficher de police de remplacement : le texte attend une fraction de seconde,
puis apparaît directement dans la bonne police.

Texte penché et net : ne jamais mettre de `filter` (ombre portée…) ni de
découpe `clip-path` sur un élément incliné qui contient du texte. Le
navigateur peindrait le texte en image avant de la pivoter : il floute.
Ombres et formes vont sur un calque à part (`::before`), derrière le texte.

## Où sont les fichiers

Le dépôt reproduit exactement le dossier
`/home/clients/<identifiant>/sites/bigbudigames.fr/` du Web FTP.
Un fichier ici = le même fichier là-bas, au même endroit.

```
index.html          page d'accueil
jeux.html           les jeux, en vignettes
jeu/                une page par jeu (edit, tornadice, camino)
catalogue.html      redirige vers jeux.html
boutique.html       redirige vers jeux.html
blog.html + blog/   le blog et ses articles
a-propos.html       à propos
contact.html        contact
newsletter.html     inscription à la newsletter (page à partager)
newsletter-merci.html, newsletter-bienvenue.html
                    étapes après l'inscription (redirections Infomaniak)
sourcing.html       sourcing
style.css           toute la mise en forme du site
assets/             images et fichiers joints
assets/equipe/      photos des collaborateurs (carrées, 720 px, sans métadonnées)
robots.txt          instructions pour les moteurs de recherche
sitemap.xml         plan du site pour les moteurs de recherche
```

Chaque modification est conservée dans l'historique : on peut revenir à
n'importe quelle version antérieure du site, à tout moment.

## Newsletter

- **Outil** : Infomaniak Newsletter (Manager → Events & Marketing → Newsletter),
  groupe « Abonnés BBG », formulaire « Inscription Site Web » (n° 26387).
- **Où est le formulaire** : accueil (3e bloc des Actualités, à la place du
  Sourcing ; ancre `#newsletter`), page News (sous les articles), contact (sous le formulaire), les trois fiches de jeux et `newsletter.html`, la page à partager
  (réseaux, festivals, QR code) : `bigbudigames.fr/newsletter.html`.
- **Redirections réglées chez Infomaniak** : `newsletter-merci.html` après
  l'envoi du formulaire, `newsletter-bienvenue.html` après le clic dans l'email
  de confirmation. Ne pas renommer ces deux fichiers.
- **Si le formulaire est modifié chez Infomaniak**, son code d'intégration
  change : recopier l'onglet HTML (clé, champs cachés, scripts) dans les sept
  pages, en gardant l'habillage du site (le bloc `<style>` fourni n'est pas repris).
- **Le petit script placé juste après chaque formulaire est indispensable.**
  Quand un visiteur choisit son adresse dans la liste proposée par le
  navigateur, celui-ci remplit aussi les champs pièges cachés
  (`inf_email_check`, `website`) ; Infomaniak prend alors l'inscription pour
  un robot et l'écarte en silence, tout en affichant « Merci ! ». Le script
  vide ces champs à chaque saisie et avant l'envoi. À remettre si le code
  d'intégration est recopié.

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
