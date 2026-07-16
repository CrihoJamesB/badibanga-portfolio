# Architecture — badibanga.top

Documentation rétro-générée à partir du code réel (juillet 2026).

## Vue d'ensemble

Site portfolio **100% statique**, une seule page (`index.html`), sans framework ni étape de build. La navigation entre les quatre « pages » (À propos, Parcours, Portfolio, Contact) est un système d'onglets côté client : chaque `<article data-page="…">` est affiché/masqué par `script.js` selon le `data-nav-target` du bouton cliqué.

## Dépendances externes (CDN uniquement)

| Dépendance | Version | Usage |
|---|---|---|
| Ionicons | 8.0.13 (unpkg) | icônes (sidebar, services, boutons) |
| Google Fonts — Poppins | 300/400/500/600 | typographie |
| Google Maps embed | — | carte Kinshasa (page Contact) |
| FormSubmit.co | — | backend du formulaire de contact → crihojames@gmail.com |

Aucune dépendance npm. Aucun `package.json`.

## Contenu — source de vérité

Tout le contenu vient de `JAMES_DATA_EXPORT.md` (export consolidé du précédent portfolio Next.js) et du fichier `data.ts` de ce dernier. Choix éditoriaux appliqués :

- **Témoignages** : section supprimée — aucun témoignage réel n'existe (placeholders dans l'ancien code, jamais publiables).
- **Tarifs** : non publiés — la grille de l'export est marquée « à valider » par James.
- **FinTech/blockchain** : non repris — James a confirmé que cette mention était inexacte.
- **Chiffres clés** : uniquement ceux du `statisticsData` de l'ancien portfolio (6+ ans, 50+ projets, 200+ devs formés, 15+ devs dirigés).
- **Certifications** : listées sans lien de vérification (aucune credential URL n'existe dans l'ancien code — à fournir par James).

## Images des projets (`assets/images/projects/`)

- `al-legacy.webp`, `kadea-academy.webp`, `fogec.webp` : **screenshots réels** capturés le 2026-07-16 (viewport 1280×800).
- Les 8 autres (`*.svg`) : vignettes générées (nom + domaine + dégradé au thème) — les sites étaient injoignables depuis le réseau de build (ERR_CONNECTION_RESET). À remplacer par de vrais screenshots quand possible.

## JavaScript (`assets/js/script.js`)

Vanilla JS, quatre responsabilités :
1. Toggle sidebar mobile.
2. Filtres portfolio (boutons desktop + select mobile) — le filtre « Tous » est câblé sur le libellé français `tous` ; les catégories comparées sont les `data-category` en minuscules.
3. Activation du bouton d'envoi du formulaire quand `form.checkValidity()` passe.
4. Navigation onglets via `data-nav-target` (jamais par le texte du bouton — les libellés sont traduisibles sans casser la nav).

Tous les accès DOM sont gardés contre `null` : retirer une section HTML ne casse pas le script.

## Déploiement

- **Hébergement** : Vercel (`vercel.json` : cleanUrls, en-têtes de sécurité, cache immutable sur `/assets`).
- **Domaine cible** : https://badibanga.top (canonical + OG déjà configurés dans le `<head>`).

## SEO

`lang="fr"`, title/description/OG/Twitter Card alignés sur l'ancien portfolio, + JSON-LD `Person` (nouveau — absent de l'ancien site).

## Reste à faire (backlog connu)

- Remplacer les 8 vignettes SVG par de vrais screenshots.
- Ajouter le CV PDF (`/cv/` était vide dans l'ancien repo).
- Ajouter les credential URLs des certifications.
- Recueillir 2–3 vrais témoignages clients puis réintroduire la section.
- Activer le domaine badibanga.top sur le projet Vercel.
