# Prompts prêts pour Blink (blink.new)

## Prompt n°1 — création du projet (à coller tel quel, avec les screenshots 00→04 joints)

> Build a **React Native mobile app** (Expo) called **LinguaBiz** — a multilingual messaging app for entrepreneurs that connects to WhatsApp Business and translates every conversation in real time (client writes Arabic/Portuguese/Chinese, the user reads and replies in French).
>
> Follow the attached screenshots pixel-closely and the design system at the pinned DESIGN.md URL. Design language: warm premium, mint-white background `#F6FAF7`, deep forest green text `#0F3D2B`, bright green accent `#1FC16B` (CTA gradient `#2BD47D→#12A356`), serif headings (Fraunces, key words italic + green), Inter for body, squircle avatars, soft green-tinted shadows, NO entrance animations.
>
> Build first: Splash screen → 3 onboarding screens → Sign-in → WhatsApp connect screen. French UI copy exactly as in the screenshots. Use the image assets from the repo `/assets` folder.
>
> App structure after auth: bottom tab bar with 4 tabs — Messages, Contacts, Résumé IA, Réglages.

**Important** : le prompt doit contenir "React Native mobile app" dès le premier message (sinon Blink crée un projet web, et on ne peut plus changer de template ensuite).

**À joindre** : screenshots `00-splash.png` → `05-whatsapp-connect.png` + épingler avec `@` l'URL raw de `DESIGN.md`.

## Prompt n°2 — inbox + chat (joindre 06, 07)

> Now build the Messages tab: conversation list exactly like screenshot 06 (search, filter chips with active dark pill, conversation rows with squircle photo avatar + language chip "AR/PT/ZH" + green online dot, original-language preview line + translated line with green translate icon, green unread badges, dark FAB). Then the conversation screen like screenshot 07: the signature bubble contains the original message, a hairline divider, the French translation and an uppercase tag "TRADUIT DE L'ARABE · 1,4 S". Outgoing bubbles are dark green gradient with the Arabic translation under the divider. Composer has a translation-preview line, mic button and gradient send button. "Traduction automatique" toggle pill under the header.

## Prompt n°3 — vocal + résumé IA (joindre 09, 10)

> Add: (1) voice messages in the chat like screenshot 10 — waveform bubbles with duration, transcription + translation under a divider, and a recording state (red dot, timer, green waveform strip, trash, big gradient send). (2) The "Résumé IA" screen like screenshot 09 — dark green summary card with sparkle icon, 2×2 key-points cards, recommended actions list, 2×2 conversation analysis, PDF + Partager buttons. Reached from the sparkle icon in chat header and from the tab bar.

## Prompt n°4 — réglages (joindre 08)

> Build the Réglages tab like screenshot 08: profile card, dark green usage card (Plan Pro, "342 / 1 000 messages traduits", gradient progress bar, 3 stat columns), then plan cards "Gratuit 0€" and "Pro 14,99€/mois" (recommended, green border + floating badge).

## Conseils

- Un écran (ou deux) par message, toujours avec le screenshot correspondant joint.
- Épingler `@https://raw.githubusercontent.com/marketingmonpetitbureau-lab/linguabiz-app/main/DESIGN.md` dans les messages importants.
- Si Blink s'écarte du design : « Compare with the attached screenshot and fix spacing/colors to match exactly. »
