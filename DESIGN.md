# LinguaBiz — Design System (Green)

Multilingual messaging app for entrepreneurs (WhatsApp Business + real-time translation). Target: React Native (Expo). Reference screenshots in `/screenshots`, image assets in `/assets`, pixel-perfect HTML references in `/reference-html`.

## 1. Colors

| Token | Value | Usage |
|---|---|---|
| `background` | `#F6FAF7` | App background (soft mint-white) |
| `surface` | `#FFFFFF` | Cards, inputs, bubbles |
| `ink` | `#0F3D2B` | Primary text, dark elements (deep forest green) |
| `muted` | `#6C7F73` | Secondary text, icons |
| `border` | `#E1E9E2` | 1px card/input borders |
| `divider` | `#EAF1EB` | List separators, day chips |
| `accent` | `#1FC16B` | Links, active tab, highlights, badges |
| `accentSoft` | `#DFF5E8` | Selected card bg, icon-circle bg |
| `mintSoft` | `#E7F2EA` | Neutral chip/icon bg, progress track |
| `success` | `#3BB273` | Online dots, read receipts |
| `whatsapp` | `#25D366` | WhatsApp logo only |
| `recording` | `#E53E3E` | Recording dot only |

**Gradients**
- CTA buttons: `linear-gradient(135deg, #2BD47D → #12A356)`
- Dark cards (usage stats, AI summary): `linear-gradient(150deg, #17553C → #0D3526)` with a soft radial green glow (`rgba(31,193,107,.28)`) top-right
- Splash background: `linear-gradient(168deg, #0F3D2B → #0D3526 → #092A1D)`

**Shadows** (soft, tinted green — never pure black)
- Cards: `0 8-20px 20-46px rgba(15,61,43,.05-.10)`
- Dark cards: `0 18px 40px rgba(15,61,43,.25)`
- CTA: `0 10px 24px rgba(31,193,107,.35)`

## 2. Typography

- **Headings**: Fraunces (serif) 500/600 — expo: `@expo-google-fonts/fraunces`. H1 29–34px, letter-spacing -1%. Key words inside headings are *italic* + `accent` color (e.g. « votre *langue* »).
- **Body/UI**: Inter — `@expo-google-fonts/inter`. Body 13–15px, labels 600, buttons 15–16px/600.
- **Overline labels**: 9–11px, weight 700, uppercase, letter-spacing +8–11% , `muted` (e.g. "TRADUIT DE L'ARABE · 1,4 S", section titles "POINTS CLÉS").
- Arabic text: right-aligned, RTL, system font is fine.

## 3. Shape & spacing

- Screen padding: 22–24px horizontal.
- Radii: cards 16–24 · buttons 14–16 · inputs 14–15 · avatars 14–17 (rounded-square "squircle", NOT circles) · pills/chips 999.
- CTA button: full-width, height 56, radius 16, gradient, white text, arrow-right icon.
- Icons: outline style (feather-like), stroke ~1.9, `ink` colored.
- iOS status bar (9:41) + home indicator visible in mockups — in RN just use SafeAreaView.
- No animations required (client explicitly refused entrance animations). Static UI.

## 4. Core components

- **Chat bubble with translation** (signature component): ONE bubble contains original text, a hairline divider, the translation, then an overline tag ("TRADUIT DE L'ARABE · 1,4 S"). Incoming: white surface, border, bottom-left radius 6. Outgoing: dark green gradient, white text, translation line at 72% opacity, bottom-right radius 6.
- **Voice bubble**: play button (round), waveform bars (3px, rounded, played portion darker), duration, then divider + transcription/translation + tag.
- **Tab bar** (4 tabs): Messages (chat bubble icon) · Contacts · Résumé IA (4-point sparkle/star icon) · Réglages. Active tab = `accent`. Height ~82, white blurred bg, top border.
- **Conversation list item**: squircle photo avatar with tiny language flag-chip (dark, e.g. "AR") pinned top-left + green online dot; name + time; original-language preview line (muted, small); translated line (ink, 500) prefixed by a small green translate icon; unread count = green pill badge.
- **Filter chips row**: pill chips, active = dark `ink` bg + white text, fade-out mask on right edge (no visible scrollbar).
- **Plan cards**: white card; recommended plan has 1.5px `accent` border + floating "RECOMMANDÉ" gradient pill; feature rows with tiny check circles (`accentSoft` bg).
- **Usage dark card**: dark green gradient, big Fraunces number ("342 / 1 000 messages traduits"), green gradient progress bar, 3 stat columns.
- **Floating cards on photos** (onboarding): white rounded cards with strong soft shadow layered over photos (message card with avatar + AR text + translated line; social-proof pill with 3 stacked avatars).

## 5. Screens (11)

Flow: Splash → Onboarding(3) → Sign-in → WhatsApp connect → Inbox ⇄ Chat ⇄ (Résumé IA / Vocal) · Réglages.

| # | Screen | Key content |
|---|---|---|
| 00 | Splash | Dark green gradient, white squircle logo (chat bubble mark + green dot), "LinguaBiz" Fraunces, tagline "Le business, *sans frontières*", floating greeting chips (Bonjour, Hello, مرحباً, Olá, 你好), 3 loading dots |
| 01 | Onboarding — Hero | 2 tilted photos (`hero2-a.jpg`, `hero2-b.jpg`) + central translate badge + floating client message card (`av-ahmed.jpg`, AR→FR) + "+128 clients à l'étranger" pill (3 avatars). H1 "Vendez. Répondez. Dans *toutes* les langues." CTA "Suivant" |
| 02 | Onboarding — Traduction | Full-width photo `hero2-c.jpg` (spice merchant), floating chips: client AR bubble top-left, dark "Vous · Français" bubble bottom-right, central circular translate badge, "Traduit en 1,4 s" pill. H1 "Ils écrivent en arabe. Vous lisez en *français*." + 3 stat mini-cards (50+ langues · 1,4s · E2E) |
| 03 | Onboarding — Langue | 2-col grid of 8 language cards (code chip + name + region), selected = accent border + soft bg + check badge. FR selected |
| 04 | Sign-in | Centered logo, "Bienvenue", Apple + Google buttons (white, border), "ou par e-mail" divider, email + password fields, CTA "Se connecter", link "Créer un compte", legal footer |
| 05 | WhatsApp connect | Title + 3-step stepper (Numéro → Vérification → Synchronisation, step 1 active dark), white card with WhatsApp logo, country select 🇩🇿 +213 + phone input, SMS note, social proof "12 000+ pros", CTA "Recevoir le code", link "Essayer la démo" |
| 06 | Inbox | "Messages" Fraunces title + bell (badge 3) + profile avatar `av-karim.jpg`; search field; filter chips (Tous active); 6 conversations (Ahmed AR, Sofia PT, Wang ZH, Mohammed AR, Isabella IT, Carlos ES) using `av-*.jpg`; dark FAB (pencil); 4-tab bar |
| 07 | Chat | Header: avatar + "Ahmed Karim" + "Arabe ⇄ Français · en ligne" + sparkle (→ Résumé IA), phone, video icons; "Traduction automatique" pill with green toggle; bubbles with integrated translation; typing indicator; composer: + button, text input, translation preview line above ("Sera envoyé : &lt;arabic&gt;"), mic button (→ Vocal), gradient send button |
| 08 | Réglages | Profile card; dark usage card (Plan Pro, 342/1000, progress, 3 stats); plan cards Gratuit + Pro 14,99€/mois (recommended); 4-tab bar (Réglages active) |
| 09 | Résumé IA | Header + share; contact row; dark summary card (sparkle, summary text with bold key facts, "LinguaBiz IA" chip); 2×2 "Points clés" cards (intention, budget, délai, condition); "Actions recommandées" list (3, check + chevron); 2×2 analyse (Sentiment "Très positif" + bar, Engagement, Langues, Messages); PDF + Partager buttons; 4-tab bar (Résumé IA active) |
| 10 | Vocal | Chat variant: incoming + outgoing VOICE bubbles (waveform + duration + transcription/translation + tags "VOCAL TRANSCRIT ET TRADUIT DE L'ARABE" / "VOCAL TRADUIT EN ARABE · VOIX IA"); helper pill "Votre vocal sera transcrit puis traduit en arabe"; recording bar: red dot + timer 0:07 + "Enregistrement en cours…", trash button, green waveform strip, big gradient send button |

## 6. Assets (`/assets`)

| File | Use |
|---|---|
| `hero2-a.jpg` | Onboarding 01, left photo (phone-shop owner, coral shirt) |
| `hero2-b.jpg` | Onboarding 01, right photo (boutique owner, string lights) |
| `hero2-c.jpg` | Onboarding 02 hero (spice merchant) |
| `av-ahmed.jpg` `av-sofia.jpg` `av-wang.jpg` `av-mohammed.jpg` `av-isabella.jpg` `av-carlos.jpg` | Contact avatars |
| `av-karim.jpg` | Current user (profile, inbox header) |
| `onb-connect.jpg` `onb-hero-a.jpg` `onb-hero-b.jpg` | Spare warm-tone visuals |

All UI copy is in **French** (see screenshots for exact strings). Arabic/Portuguese/Chinese strings appear as message content.
