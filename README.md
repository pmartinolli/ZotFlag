# ZotFlag
A Zotero plugin to index tags automatically based on authors, publishers, DOI, journals and keywords found in csv concordance tables.

# In French
Extension Zotero (7 à 10) qui ajoute automatiquement des marqueurs aux références sélectionnées
quand leurs métadonnées correspondent à des listes tenues dans des fichiers CSV.
Cahier des charges : https://pmartinolli.github.io/ZotFlag/ (Pascal Martinolli, 2025).

## Langues
L'interface (menu, messages, paramètres, fichiers modèles) suit la langue choisie dans Zotero :
anglais, français, espagnol, allemand, italien, portugais (Brésil et Portugal), néerlandais, japonais,
chinois simplifié. Pour toute autre langue, ZotFlag s'affiche en anglais (ou dans la variante la plus
proche). Les en-têtes de colonnes CSV sont reconnus dans toutes ces langues (Marqueur / Marker /
Marcador / Markierung…, Cible / Target / Objetivo / Ziel…) : les fichiers sont partageables.
Pour ajouter une langue : copier `locale/en-US/zotflag.ftl` dans `locale/<code>/` et le traduire.

## Installation
Zotero > Outils > Plugins (Extensions) > roue dentée > « Install Plugin From File… » > `zotflag-1.1.0.xpi`.

## Paramétrage
Zotero > Paramètres > ZotFlag :
- **Emplacement des fichiers CSV** (bouton Parcourir…) ;
- nom de la colonne des marqueurs et de la colonne cible (vide = nom par défaut de la langue de Zotero, ex. `Marqueur`/`Cible` en français, `Marker`/`Target` en anglais) ;
- bouton pour créer les fichiers CSV modèles manquants.

## Fichiers CSV (dans le dossier choisi)
| Fichier | Comparé à |
|---|---|
| `journals.csv` | titre de la publication (revue, livre, actes, site…) et abréviation de revue |
| `publishers.csv` | maison d'édition (et champs équivalents : université, institution, label…) |
| `persons.csv` | tous les créateurs (auteur, éditeur, autres rôles), cible au format `nom, prénom` |
| `dois.csv` | DOI (champ DOI, ligne `DOI:` du champ Extra, URL doi.org) |
| `metadata.csv` | tous les champs (mot ou expression entière) et les marqueurs existants (égalité stricte) |

Colonnes : `Marqueur`, `Cible`, et toute autre colonne (ex. `Notes`) ignorée. Une ligne = un marqueur
pour une cible ; répéter la ligne pour plusieurs marqueurs ou plusieurs variantes.
Séparateur virgule, point-virgule ou tabulation détecté automatiquement ; UTF-8 (repli Windows-1252).

## Utilisation
Sélectionner une, plusieurs ou toutes les références > clic droit > **ZotFlag** >
- Marquage : maisons d'édition, revues, etc. (journals.csv puis publishers.csv)
- Marquage : auteurs, éditeurs, etc. (persons.csv)
- Marquage : termes dans les métadonnées (metadata.csv)
- Marquage : articles (dois.csv)
- Marquage : tout (tous les traitements ; metadata.csv en dernier)

## Règles de repérage (strict uniquement)
- Pas de troncature, pas de variantes automatiques : créer soi-même une ligne par variante.
- Sont ignorés : la casse, les accents et ligatures (é = e, ç = c, œ = oe), les espaces multiples,
  apostrophes/tirets typographiques, balises `<i>` etc.
- Personnes : `Roux, D` repère Roux D (et « Roux D. ») mais pas Roux Damien. Une cible sans virgule repère
  un nom en un seul champ (institution).
- metadata.csv : le terme doit apparaître comme mot/expression entier (« jeu de rôle » ne repère pas
  « jeux de rôle » ni « jeu de rôles »). Une cible qui est un marqueur (ex. `_jeu de rôle`) permet
  d'ajouter un générique (`_JEU`) ; les ajouts s'enchaînent (plusieurs niveaux possibles).
- Un marqueur déjà présent n'est jamais dupliqué. Les bibliothèques en lecture seule sont ignorées.

## Licence
GPL-3.0-or-later. Auteurs : Pascal Martinolli (cahier des charges) ; code généré avec Claude.
