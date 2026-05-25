# ☕ MiMoBrew

### AI Coffee & Tea Advisor — Powered by Xiaomi MiMo V2.5

Tell MiMo how you feel. Get a precisely calibrated brew recommendation — with method, temperature, ratio, steep time, and flavor profile.

[![Live Demo](https://img.shields.io/badge/Live-Demo-000?style=for-the-badge&logo=github)](https://gyoomei.github.io/mimobrew/)
[![Try Now](https://img.shields.io/badge/Try-Now-d4882a?style=for-the-badge&logo=googlechrome)](https://gyoomei.github.io/mimobrew/)
[![AI](https://img.shields.io/badge/AI-Xiaomi%20MiMo%20V2.5-f97316?style=for-the-badge)](https://huggingface.co/XiaomiMiMo)
[![Drinks](https://img.shields.io/badge/Drinks-Coffee%20%26%20Tea-8b6914?style=for-the-badge)](#the-brew-palette)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)

---

## 📖 The Problem

Every coffee app tells you the difference between a latte and a cappuccino. None of them tell you what to drink when you're stressed at 11pm on a rainy Tuesday and need to sleep in 3 hours. Generic recommendations ignore mood, time, weather, and context — the things that actually determine what brew will hit right.

**MiMoBrew fixes that.** Describe how you feel. MiMo V2.5 picks a specific drink with precise brewing parameters tailored to your current state.

---

## ✨ How it works

```
You feel:     😰 Stressed · 🌙 Night · 🌧️ Rainy
              "have a big meeting tomorrow morning"

MiMo writes:  🍵 Chamomile & Lavender Honey Blend
              ─────────────────────────────────
              Method:      Steep (covered)
              Temperature: 95°C
              Ratio:       2g / 200ml
              Steep Time:  5:00
              Amount:      2g dried chamomile + 3 lavender buds

              Tagline: "The rain outside needs a quiet companion
              inside — this blend tells your nervous system that
              tomorrow will wait."

              Flavor: floral · honey · apple · earthy · smooth · calming
              Tip: Cover while steeping — chamomile's essential oils
              evaporate quickly.
```

**That's the entire UX** — feel, brew, sip, repeat.

---

## 🎯 Core Features

| Capability | Detail |
|---|---|
| ☕ **Mood-to-Brew** | 8 moods (tired, stressed, focused, cozy, energetic, creative, social, calm) → specific drink |
| 🌤️ **Context Aware** | Time of day, weather, and free-text situation factored into recommendation |
| 🎯 **Precise Parameters** | Method, temperature (°C), ratio, steep time, amount — barista-grade precision |
| 🎨 **Flavor Wheel** | Canvas 2D radar chart: bitter, sweet, acidic, earthy, floral, creamy, spicy, fruity |
| ⏱️ **Brew Timer** | Built-in countdown timer with pause/reset — steep time auto-set from recommendation |
| 📖 **Brew Journal** | Save up to 30 recommendations to localStorage with mood + context metadata |
| 💬 **Ask MiMo** | Chat about brewing techniques, origins, tea varieties, pairing suggestions |
| ☕ **Specific Drinks** | "Ethiopian Yirgacheffe Pour-over" not just "pour-over" — real variety names |
| 🌗 **Dark/Light Mode** | Warm amber palette, WCAG-AA compliant |
| 🌐 **Bilingual EN/ID** | Full Indonesian + English |
| 📱 **Mobile Responsive** | Fluid from 375px to 1920px |

---

## 🍵 The Brew Palette

| Mood | Time | Drink Style |
|---|---|---|
| 😴 Tired | Morning | Double espresso, strong pour-over |
| 😰 Stressed | Evening | Chamomile, lavender tea, warm milk |
| 🎯 Focused | Afternoon | Matcha latte, Yerba Mate |
| 🛋️ Cozy | Night | Chai latte, hot chocolate, genmaicha |
| ⚡ Energetic | Morning | Cold brew, Vietnamese iced coffee |
| 🎨 Creative | Afternoon | Ethiopian single-origin, oolong |
| 👥 Social | Evening | Cortado, cappuccino, jasmine tea |
| 🧘 Calm | Night | Hojicha, rooibos, butterfly pea flower |

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────┐
│  Input: Mood chips + Context pills + Free text              │
│                          ↓                                   │
│  Prompt Builder           →  mood+context → system prompt    │
│                          ↓                                   │
│  MiMo V2.5 (Pollinations.ai) → JSON with drink parameters   │
│                          ↓                                   │
│  Renderer                 →  drink card + brew params grid   │
│                          ↓                                   │
│  Flavor Wheel (Canvas 2D) →  8-axis radar chart              │
│                          ↓                                   │
│  Timer Engine             →  countdown from steep time       │
│                          ↓                                   │
│  Journal (localStorage)   →  save + browse history           │
└─────────────────────────────────────────────────────────────┘
```

**Zero backend.** Everything runs client-side. No API key. No tracking.

---

## 💡 Architecture Decisions

**Why mood-based instead of taste-based?**
People don't know what coffee they want — they know how they feel. "I'm tired and it's raining" is a better input than "I like medium roast." Mood-first design makes the tool accessible to non-coffee-nerds.

**Why specific drink names?**
"Pour-over" is a method. "Ethiopian Yirgacheffe Pour-over" is an experience. Specificity makes recommendations feel crafted, not generic. It also educates users about coffee/tea varieties.

**Why a brew timer?**
Steep time is the most commonly miscalculated parameter in home brewing. An integrated timer removes the guesswork and connects the recommendation to execution.

**Why canvas for the flavor wheel?**
An 8-axis radar chart with smooth curves and data points needs Canvas 2D — CSS/SVG would require complex polygon math for each axis.

---

## 🧪 Try these examples

| Mood | Context | Expected |
|---|---|---|
| 😴 Tired + ⚡ Energetic | Morning, Hot | Cold brew or Vietnamese iced coffee |
| 😰 Stressed + 🧘 Calm | Night, Rainy | Chamomile or lavender tea |
| 🎯 Focused | Afternoon, Any | Matcha or Yerba Mate |
| 🛋️ Cozy | Evening, Cold | Chai latte or genmaicha |
| 🎨 Creative | Afternoon, Any | Ethiopian single-origin or oolong |
| 👥 Social | Evening, Any | Cortado or cappuccino |

---

## 🛠️ Stack

- **Frontend:** Vanilla JavaScript, single HTML file (~35KB)
- **AI:** [Xiaomi MiMo V2.5](https://github.com/XiaomiMiMo) via [Pollinations.ai](https://text.pollinations.ai/) — free, no API key
- **Fonts:** [Sora](https://fonts.google.com/specimen/Sora) + [Nunito](https://fonts.google.com/specimen/Nunito) + [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono)
- **Storage:** localStorage for brew journal
- **Hosting:** GitHub Pages (zero infra cost)

---

## 🚀 Quick Start

```bash
git clone https://github.com/gyoomei/mimobrew.git
cd mimobrew
python3 -m http.server 8080
# Open http://localhost:8080
```

Or just visit the [live demo](https://gyoomei.github.io/mimobrew/).

---

## 📄 License

MIT — brew freely, share widely.

---

**Built with 🧠 [Xiaomi MiMo V2.5](https://github.com/XiaomiMiMo) · Submitted to the [Xiaomi MiMo 100T program](https://100t.xiaomimimo.com/)**
