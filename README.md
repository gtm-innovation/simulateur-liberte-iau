# Simulateur — Âge de liberté financière (lead magnet IAU)

`index.html` est un **fragment injectable**, pas une page autonome : il se colle tel quel
dans un bloc HTML personnalisé Gutenberg. Il ne contient ni `doctype`, ni `<html>`,
ni `<head>`, ni `<body>`, ni header, ni footer — le thème Astra les fournit.

## Intégration

1. Coller le contenu de `index.html` dans un bloc HTML personnalisé de la page.
2. Mettre la page en **noindex** (Rank Math).
3. Ne rien modifier dans le fragment : l'endpoint est déjà configuré.

## Contraintes respectées

- Racine versionnée `.mrlib.v1` — tous les sélecteurs sont préfixés, aucune règle nue,
  donc aucun risque de repeindre le reste du site.
- Variables CSS sur le conteneur, jamais sur `:root`.
- Responsive en `@container` (largeur de la colonne WordPress, pas de l'écran).
- Aucune police chargée : la pile du thème est héritée.
- Tous les `id` sont préfixés `mrlib-`.

## Backend

Le formulaire poste vers le Worker Cloudflare `mric-rapport-impots`
(`calculator: "liberte-iau"`), qui inscrit le lead dans Beehiiv avec les custom fields
attendus par la séquence, puis le fait entrer dans l'automation IAU pour le segment
`standard`. Les segments `zero` et `libre` sont seulement tagués.
