# LinguaBiz — Parcours & règles produit (MVP)

**Règle d'or** : l'utilisateur doit voir un message traduit dans les **60 secondes** après l'installation. Tout ce qui retarde ça est optionnel ou supprimé.

## 1. Premier lancement

```
Splash (2 s) → Onboarding 1 (hero) → Onboarding 2 (traduction) → Onboarding 3 (langue)
   → [Essayer la démo]  →  DÉMO CHAT (sans compte)   ← le chemin par défaut, mis en avant
   → [Créer un compte]  →  Sign-in
```

- « Passer » sur chaque écran d'onboarding → va au choix langue (écran 3, le seul utile fonctionnellement).
- **Mode démo** : une conversation pré-remplie (Sofia, PT→FR) où l'utilisateur peut taper un message et voir la traduction simulée arriver. Bandeau haut « Mode démo — S'inscrire ». Aucune inscription requise.
- La **connexion WhatsApp n'est PAS dans le parcours initial**. Elle vit dans Réglages → « Connecter WhatsApp Business » (et une carte suggestion dans l'inbox). L'app démarre en messagerie interne.

## 2. Navigation

- Tab bar 4 onglets : **Messages · Contacts · Résumé IA · Réglages** (validée).
- Une action principale par écran. Le FAB de l'inbox = nouvelle conversation.
- Chat : micro = vocal, étoile = résumé IA de CETTE conversation. Onglet Résumé IA = liste des résumés.

## 3. États à couvrir (chaque écran)

| Écran | Vide | Chargement | Erreur / limite |
|---|---|---|---|
| Inbox | Illustration + « Invitez votre premier client » + CTA | Skeleton rows | Bandeau hors-ligne |
| Chat | Suggestions de premiers messages | Bulle « traduction… » (3 points) | « Traduction indisponible — réessayer » ; envoi conservé |
| Résumé IA | « Pas encore de résumé — ouvrez une conversation » | Carte skeleton | Quota atteint → carte upgrade |
| Vocal | — | Onde + « transcription… » | Micro refusé → guide réglages système |

- **Quota gratuit (50 messages/mois)** : compteur discret dans Réglages ; à 80 % un bandeau doux dans le chat ; à 100 % le champ de saisie affiche la carte « Passer à Pro » (le message reste éditable, jamais perdu).
- **Hors-ligne** : les messages s'envoient en file d'attente, traduits au retour du réseau.

## 4. Simplifications assumées (MVP)

- Pas d'appels voix/vidéo (icônes présentes → « Bientôt disponible »).
- Pas de groupes. 1 conversation = 1 contact.
- Langue de l'app = langue du device (modifiable Réglages) ; le choix d'onboarding = langue de TRADUCTION de l'utilisateur.
- Arabe : contenu RTL dans les bulles uniquement, l'UI reste LTR (standard WhatsApp).

## 5. Phases techniques

1. **Phase 1** : app Expo complète, données mockées, mode démo fonctionnel (traduction simulée).
2. **Phase 2** : Supabase — auth (email/Apple/Google), conversations & messages temps réel, traduction réelle (Edge Function → DeepL/Claude), quotas.
3. **Phase 3** : vocal (Whisper STT + traduction + TTS) et Résumé IA réel.
4. **Phase 4** : WhatsApp Business Cloud API + abonnements RevenueCat (Pro 14,99 €/mois).
5. **Publication** : EAS Build/Submit, screenshots via AppLaunchFlow MCP, fiches App Store / Play Store.
