# Mémory — v1

PWA de mémoire vocale : un tap, une session d'écoute continue, chaque phrase devient une note relisible à voix haute.

## Fonctionnement

- **Un tap sur le gros bouton** → session d'écoute. L'app dit « Je t'écoute ».
- Chaque phrase prononcée = une note enregistrée, confirmée à voix haute (« C'est noté »).
- **Arrêt** : dire « terminé mémo » ou « fin de note », OU re-taper le bouton, OU 30 s de silence.
- **Écouter une note** : bouton 🔊 sur la carte.
- **Supprimer** : 🗑️ puis maintenir le bouton rouge 3 secondes (anti-erreur).
- Fonctionne hors-ligne une fois installée (service worker).

## Contraintes techniques

- **Chrome Android / Chrome desktop uniquement** (API Web Speech). Firefox non supporté.
- **HTTPS obligatoire** pour le micro → GitHub Pages convient parfaitement.
- Notes stockées en **localStorage local à l'appareil** (pas de synchro téléphone/PC en v1).

## Déploiement (GitHub Pages)

1. Créer un dépôt, pousser ces 5 fichiers à la racine.
2. Settings → Pages → Source : branche `main`, dossier `/ (root)`.
3. Ouvrir l'URL en HTTPS dans Chrome sur le téléphone.
4. Menu Chrome → « Ajouter à l'écran d'accueil » → l'icône Mémory apparaît.
5. Premier lancement : autoriser le micro (une seule fois).

## Backlog v1.1 (non inclus volontairement)

- Synchro Supabase téléphone ↔ PC
- Mode question à l'IA (« qu'est-ce que je devais faire ? »)
- Rappels / notifications vocales programmées
- Lancement « Ok Google, ouvre Mémory »
