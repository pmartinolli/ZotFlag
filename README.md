# ZotFlag
A Zotero plugin to index tags automatically based on authors, publishers, DOI, journals and keywords found in csv concordance tables.

---

**In English**

Zotero Extension (7 to 10) that automatically adds tags to selected references when their metadata matches lists kept in CSV files.

Specifications: [https://pmartinolli.github.io/ZotFlag/](https://pmartinolli.github.io/ZotFlag_cahierdescharges/) (Pascal Martinolli, 2025).

### Languages

The interface (menu, messages, settings, template files) follows the language selected in Zotero: English, French, Spanish, German, Italian, Portuguese (Brazil and Portugal), Dutch, Japanese, Simplified Chinese. For any other language, ZotFlag is displayed in English (or in the closest variant). CSV column headers are recognized in all these languages (Marqueur / Marker / Marcador / Markierung…, Cible / Target / Objetivo / Ziel…): files are shareable.

To add a language: copy `locale/en-US/zotflag.ftl` to `locale/<code>/` and translate it.

### Installation

Zotero > Tools > Plugins > gear icon > "Install Plugin From File…" > `zotflag-1.1.0.xpi`.

### Configuration

Zotero > Settings > ZotFlag:

* CSV file location (Browse… button);
* Name of the tag column and the target column (empty = default name for the Zotero language, e.g., Marqueur/Cible in French, Marker/Target in English);
* Button to create missing model/template CSV files.

### CSV Files (in the selected folder)

| File | Compared to |
| --- | --- |
| `journals.csv` | Publication title (journal, book, proceedings, website…) and journal abbreviation |
| `publishers.csv` | Publisher (and equivalent fields: university, institution, label…) |
| `persons.csv` | All creators (author, editor, other roles), target in *Last Name, First Name* format |
| `dois.csv` | DOI (DOI field, `DOI:` line in the Extra field, doi.org URL) |
| `metadata.csv` | All fields (whole word or phrase) and existing tags (strict equality) |

**Columns:** Marker/Tag, Target, and any other column (e.g., Notes) ignored. One line = one tag for one target; repeat the line for multiple tags or multiple variants.

Comma, semicolon, or tab separator detected automatically; UTF-8 (fallback Windows-1252).

### Usage

Select one, several, or all references > right-click > ZotFlag >

* Flagging: publishers, journals, etc. (`journals.csv` then `publishers.csv`)
* Flagging: authors, editors, etc. (`persons.csv`)
* Flagging: terms in metadata (`metadata.csv`)
* Flagging: articles (`dois.csv`)
* Flagging: all (all processes; `metadata.csv` last)

### Matching Rules (Strict Only)

* No truncation, no automatic variants: create one line per variant yourself.
* Ignored: case, accents and ligatures (é = e, ç = c, œ = oe), multiple spaces, typographic apostrophes/hyphens, HTML tags like `<i>`, etc.
* **Persons:** `Roux, D` matches `Roux D` (and "Roux D.") but not `Roux Damien`. A target without a comma matches a name in a single field (institution).
* **`metadata.csv`:** The term must appear as a whole word/phrase ("jeu de rôle" does not match "jeux de rôle" nor "jeu de rôles"). A target that is an existing tag (e.g., `_jeu de rôle`) allows adding a generic tag (e.g., `_JEU`); additions can chain together (multiple levels possible).
* An already existing tag is never duplicated. Read-only libraries are ignored.

### License

GPL-3.0-or-later. Authors: Pascal Martinolli (specifications); code generated with Claude.

*In French*
Extension Zotero (7 à 10) qui ajoute automatiquement des marqueurs aux références sélectionnées
quand leurs métadonnées correspondent à des listes tenues dans des fichiers CSV.
Cahier des charges : [https://pmartinolli.github.io/ZotFlag/](https://pmartinolli.github.io/ZotFlag_cahierdescharges/) (Pascal Martinolli, 2025).

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
