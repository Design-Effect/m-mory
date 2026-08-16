# Memory — v1

PWA de mémoire vocale : un tap (ou « Ouvre Memory »), une session d'écoute continue, tout ce qui est dit devient une note relisible à voix haute.

Conçue pour un usage à un seul doigt, avec le moins de navigation possible : un seul écran, interaction vocale au maximum.

## Fonctionnement

- **Démarrer** : un tap sur le gros bouton, ou « Ok Google, ouvre Memory » — si le micro est autorisé en permanence, la session démarre toute seule à l'ouverture.
- **Parler** : aussi longtemps qu'on veut, avec des pauses naturelles. Tout s'accumule dans **une seule note** (un bip discret confirme chaque bout capté, le texte s'affiche en direct).
- **Arrêter** : dire **« terminé mémo »** ou **« fin de note »**, re-taper le bouton, ou 60 s de silence. Dans tous les cas, tout ce qui a été dit est sauvé.
- **Corriger en parlant** : dire **« efface ça »** annule ce qui vient d'être dit ; **« efface tout »** ou **« on recommence »** vide la note en cours et repart de zéro. Un bip grave confirme l'effacement.
- **📖 Ma journée** : relit à voix haute toutes les notes du jour, dans l'ordre chronologique. Déclenchable aussi à la voix pendant une session : **« lis ma journée »**.
- **🔍 Chercher** : l'app demande « Quel mot ? », puis lit les notes qui le contiennent (5 max à voix haute, le reste filtré à l'écran). À la voix pendant une session : **« cherche le mot [X] »** lance directement la recherche sur X.
- **Écouter une note** : bouton 🔊 sur la carte. Les notes sont regroupées par jour (Aujourd'hui / Hier / date).
- **Supprimer** : 🗑️ puis **maintenir le bouton rouge 3 secondes** (protection contre les suppressions accidentelles).
- Fonctionne hors-ligne une fois installée (service worker).

## Contraintes techniques

- **Chrome Android / Chrome desktop uniquement** (API Web Speech). Firefox non supporté.
- **HTTPS obligatoire** pour le micro → GitHub Pages convient parfaitement.
- Notes stockées en **localStorage local à l'appareil** (pas de synchro téléphone/PC en v1).
- Le nom d'app est volontairement **« Memory » sans accent** dans le manifest : Gemini / Google Assistant ne retrouvent pas le nom avec accent.

## Déploiement (GitHub Pages)

1. Créer un dépôt, pousser ces fichiers à la racine.
2. Settings → Pages → Source : branche `main`, dossier `/ (root)`.
3. Ouvrir l'URL en HTTPS dans Chrome sur le téléphone.
4. Menu Chrome ⋮ → **« Installer l'application »** (pas « Ajouter à l'écran d'accueil » si les deux sont proposés) — nécessaire pour que Gemini puisse ouvrir l'app par la voix.
5. Premier lancement : autoriser le micro en choisissant **« Autoriser »** (pas « cette fois seulement ») — nécessaire pour l'auto-démarrage vocal.

## Mise à jour de l'app

À chaque modification, incrémenter la version du cache dans `sw.js` (`memory-vX`), pousser, puis fermer/rouvrir l'app sur le téléphone. Si le nom ou l'icône changent dans le manifest, désinstaller et réinstaller l'app.

## Ouverture vocale (Gemini)

- Dire « Ouvre Memory ». Si Gemini ne trouve pas l'app : vérifier qu'elle apparaît dans Paramètres Android → Applications (sinon la réinstaller via « Installer l'application »).
- Si Gemini n'ouvre aucune app : Gemini → profil → Paramètres → Applis connectées → vérifier « Utilitaires », et vérifier que « Conserver l'activité » est activé dans le menu Activité.

## Backlog v1.1 (non inclus volontairement)

- Synchro Supabase téléphone ↔ PC
- Mode question à l'IA (« qu'est-ce que je devais faire ? »)
- Rappels / notifications vocales programmées
