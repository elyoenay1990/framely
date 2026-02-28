# ð¬ FRAMELY

```
âââââââââââââââ  ââââââ ââââ   âââââââââââââââ  âââ   âââ
âââââââââââââââââââââââââââââ ââââââââââââââââ  ââââ ââââ
ââââââ  âââââââââââââââââââââââââââââââââ  âââ   âââââââ 
ââââââ  âââââââââââââââââââââââââââââââââ  âââ    âââââ  
âââ     âââ  ââââââ  ââââââ âââ ââââââââââââââââââââââ   
âââ     âââ  ââââââ  ââââââ     ââââââââââââââââââââââ   
```

> **Turn your story into cinema.**

Framely is a cinematic web application that transforms your stories into video content using AI. Designed with a dark, immersive aesthetic inspired by the world's greatest streaming platforms, Framely puts the power of AI-driven video production in the hands of storytellers, creators, and visionaries.

---

## â¨ Features

- ð **Multi-language Support** â Seamlessly switch between Spanish, English, French, German, Italian, and Portuguese (ES / EN / FR / DE / IT / PT)
- ð¨ **Cinematic Dark UI with Glassmorphism Design** â Deeply immersive interface featuring frosted glass panels, rich dark backgrounds, and cinematic color grading
- ð **Story Creation with Character & Setting Descriptions** â Craft your narrative with detailed character profiles and rich world-building fields powered by an AI twin agent
- ð¼ï¸ **Reference Image Upload** â Upload up to 3 reference images to guide the visual style, character look, or scene composition of your video
- â±ï¸ **Multiple Duration Tiers** â From a quick Demo clip to the full Ãpico experience, choose the duration that fits your vision and budget
- ð¡ **Multi-Channel Distribution** â Distribute your content across TikTok, YouTube, Email, WhatsApp, and more, all from one place
- ðº **Netflix-Style Story History Viewer** â Browse your past stories and generated videos in a beautifully curated, card-based history gallery
- ðµ **Spotify-Style Music Selector** â Choose the perfect cinematic soundtrack for your video from a curated library of moods and genres

---

## ð¸ Screenshots

> _Screenshots and demo GIFs coming soon._

| Story Creator | History Viewer | Music Selector |
|:---:|:---:|:---:|
| *(placeholder)* | *(placeholder)* | *(placeholder)* |

---

## ð Getting Started

Framely is a zero-dependency, pure frontend application. No build tools, no package manager, no compilation step required.

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/framely.git
cd framely
```

### 2. Open Locally

Simply open `index.html` in your browser:

```bash
# macOS
open index.html

# Linux
xdg-open index.html

# Windows
start index.html
```

Or serve it with any static file server:

```bash
# Using Python
python3 -m http.server 8080

# Using Node.js (npx)
npx serve .
```

Then visit `http://localhost:8080`.

### 3. Deploy

Framely can be deployed to any static hosting provider in seconds:

#### GitHub Pages
1. Push your repository to GitHub
2. Go to **Settings â Pages**
3. Select your branch (`main`) and root folder (`/`)
4. Your app will be live at `https://your-username.github.io/framely`

#### Netlify
1. Drag and drop the project folder into [app.netlify.com/drop](https://app.netlify.com/drop)
2. Or connect your GitHub repo for continuous deployment

#### Vercel
```bash
npx vercel --prod
```
Or connect the repository through the [Vercel dashboard](https://vercel.com/dashboard).

---

## âï¸ Configuration

Framely communicates with external AI and data services via configurable webhook and API URLs. These can be set directly inside the JavaScript source files.

### Webhook URL â Story Creator Twin Agent

This endpoint receives the story payload and triggers the AI video generation pipeline.

Open `js/config.js` (or the relevant configuration block in `index.html`) and set:

```javascript
// The endpoint for your Story Creator Twin agent
const WEBHOOK_URL = 'https://your-agent-endpoint.com/webhook/story-creator';
```

The following payload is sent as a `POST` request with `Content-Type: application/json`:

```json
{
  "title": "Story title",
  "story": "Full story text...",
  "characters": "Character descriptions...",
  "setting": "Scene and world description...",
  "duration": "Ã©pico",
  "language": "en",
  "channels": ["tiktok", "youtube"],
  "music": "cinematic-epic",
  "referenceImages": ["base64...", "base64..."]
}
```

### History API URL

This endpoint returns previously generated stories and videos to populate the Netflix-style history viewer.

```javascript
// The endpoint for fetching story history
const HISTORY_API_URL = 'https://your-api-endpoint.com/api/stories/history';
```

Expected response format:

```json
{
  "stories": [
    {
      "id": "abc123",
      "title": "The Last Signal",
      "thumbnail": "https://cdn.example.com/thumb.jpg",
      "duration": "Ã©pico",
      "createdAt": "2024-11-15T18:32:00Z",
      "videoUrl": "https://cdn.example.com/video.mp4",
      "language": "en"
    }
  ]
}
```

> **Note:** If no API URLs are configured, Framely gracefully falls back to demo/mock data so the UI remains fully explorable without a backend.

---

## ð ï¸ Tech Stack

Framely is intentionally built with **zero external dependencies** â no frameworks, no libraries, no bundlers. Just the open web platform at its finest.

| Technology | Purpose |
|---|---|
| **HTML5** | Semantic structure, custom data attributes, file input APIs |
| **CSS3** | Glassmorphism, custom properties (variables), animations, grid & flexbox layouts |
| **Vanilla JavaScript (ES6+)** | DOM manipulation, Fetch API, dynamic i18n, state management |
| **CSS Custom Properties** | Design token system for theming |
| **Web APIs** | FileReader API (image upload), Fetch API (webhooks), LocalStorage (persistence) |

---

## ð¨ Design Tokens

All visual constants are defined as CSS custom properties on the `:root` selector, making the design system fully themeable.

### Colors

```css
:root {
  /* Backgrounds */
  --color-bg-primary:      #0a0a0f;   /* Deep void black */
  --color-bg-secondary:    #12121a;   /* Dark surface */
  --color-bg-glass:        rgba(255, 255, 255, 0.04); /* Glassmorphism base */
  --color-bg-glass-hover:  rgba(255, 255, 255, 0.08);

  /* Brand / Accent */
  --color-accent-gold:     #c9a84c;   /* Cinematic gold */
  --color-accent-amber:    #e8b84b;   /* Warm amber highlight */
  --color-accent-crimson:  #8b1a1a;   /* Deep cinematic red */
  --color-accent-purple:   #6c3483;   /* Atmospheric purple */

  /* Text */
  --color-text-primary:    #f0ece4;   /* Warm off-white */
  --color-text-secondary:  #a89880;   /* Muted parchment */
  --color-text-muted:      #5c5248;   /* Dim label text */

  /* Borders */
  --color-border-glass:    rgba(201, 168, 76, 0.15);  /* Gold glass border */
  --color-border-subtle:   rgba(255, 255, 255, 0.06);

  /* States */
  --color-success:         #2ecc71;
  --color-error:           #e74c3c;
  --color-warning:         #f39c12;
}
```

### Typography

```css
:root {
  /* Font Families */
  --font-display:   'Playfair Display', 'Georgia', serif;     /* Cinematic headings */
  --font-body:      'Inter', 'Helvetica Neue', sans-serif;    /* Clean body copy */
  --font-mono:      'JetBrains Mono', 'Courier New', monospace; /* Code / labels */

  /* Font Sizes (fluid scale) */
  --text-xs:   0.75rem;    /* 12px */
  --text-sm:   0.875rem;   /* 14px */
  --text-base: 1rem;       /* 16px */
  --text-lg:   1.125rem;   /* 18px */
  --text-xl:   1.25rem;    /* 20px */
  --text-2xl:  1.5rem;     /* 24px */
  --text-3xl:  1.875rem;   /* 30px */
  --text-4xl:  2.25rem;    /* 36px */
  --text-hero: clamp(2.5rem, 6vw, 5rem); /* Responsive hero text */

  /* Font Weights */
  --weight-regular:    400;
  --weight-medium:     500;
  --weight-semibold:   600;
  --weight-bold:       700;
  --weight-black:      900;

  /* Letter Spacing */
  --tracking-tight:  -0.025em;
  --tracking-wide:    0.05em;
  --tracking-widest:  0.2em;   /* Used for uppercase labels */
}
```

### Spacing & Radii

```css
:root {
  --radius-sm:   6px;
  --radius-md:   12px;
  --radius-lg:   20px;
  --radius-xl:   32px;
  --radius-full: 9999px;

  --blur-glass:  blur(20px);
  --blur-heavy:  blur(60px);

  --shadow-glow-gold: 0 0 40px rgba(201, 168, 76, 0.2);
  --shadow-card:      0 8px 32px rgba(0, 0, 0, 0.6);
}
```

---

## ð Project Structure

```
framely/
â
âââ index.html              # Main entry point â single-page application shell
â
âââ css/
â   âââ main.css            # Global styles, resets, design tokens
â   âââ components.css      # Reusable UI components (cards, buttons, modals)
â   âââ story-creator.css   # Story creation form styles
â   âââ history.css         # Netflix-style history viewer styles
â   âââ music-selector.css  # Spotify-style music selector styles
â
âââ js/
â   âââ config.js           # âï¸  WEBHOOK_URL, HISTORY_API_URL, global config
â   âââ app.js              # Application bootstrap and routing
â   âââ i18n.js             # Internationalization (ES/EN/FR/DE/IT/PT)
â   âââ story-creator.js    # Story form logic, image upload, submission
â   âââ history.js          # History viewer, card rendering, filtering
â   âââ music-selector.js   # Music library, mood filtering, preview
â   âââ utils.js            # Shared helpers (debounce, API calls, etc.)
â
âââ assets/
â   âââ fonts/              # Self-hosted font files (optional, falls back to Google Fonts)
â   âââ icons/              # SVG icon set
â   âââ images/
â   â   âââ logo.svg        # Framely wordmark
â   â   âââ og-image.png    # Open Graph preview image
â   âââ audio/
â       âââ previews/       # 30-second music mood preview clips
â
âââ locales/
â   âââ en.json             # English strings
â   âââ es.json             # Spanish strings
â   âââ fr.json             # French strings
â   âââ de.json             # German strings
â   âââ it.json             # Italian strings
â   âââ pt.json             # Portuguese strings
â
âââ .github/
â   âââ workflows/
â       âââ deploy.yml      # GitHub Pages auto-deploy workflow
â
âââ LICENSE                 # MIT License
âââ README.md               # You are here
```

---

## ð Duration Tiers

| Tier | Label | Duration | Best For |
|---|---|---|---|
| ðï¸ | **Demo** | ~15 sec | Quick proof of concept |
| ð± | **Short** | ~30 sec | TikTok / Reels / Shorts |
| ð¬ | **Standard** | ~60 sec | Social media posts |
| ð­ | **Extended** | ~2 min | YouTube / storytelling |
| ð | **Ãpico** | ~5 min | Full cinematic experience |

---

## ð Supported Languages

| Code | Language | Status |
|---|---|---|
| `en` | English | â Full support |
| `es` | EspaÃ±ol | â Full support |
| `fr` | FranÃ§ais | â Full support |
| `de` | Deutsch | â Full support |
| `it` | Italiano | â Full support |
| `pt` | PortuguÃªs | â Full support |

Language is auto-detected from browser settings and can be toggled in the UI at any time.

---

## ð¡ Distribution Channels

Framely supports one-click export targeting for the following platforms:

- ð± **TikTok** â Vertical 9:16, under 60s optimized
- â¶ï¸ **YouTube** â Landscape 16:9, full-length support
- ð§ **Email** â Compressed MP4 with thumbnail fallback
- ð¬ **WhatsApp** â Mobile-optimized, size-capped
- ð¸ **Instagram** â Square and Reels format support
- ð¦ **X / Twitter** â Under 2:20 optimized

---

## ð¤ Contributing

Contributions are welcome! Here's how to get involved:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature-name`
3. Commit your changes: `git commit -m 'feat: add your feature'`
4. Push to the branch: `git push origin feature/your-feature-name`
5. Open a Pull Request

Please follow the existing code style â no external dependencies, no build steps.

---

## ð License

This project is licensed under the **MIT License**.

```
MIT License

Copyright (c) 2024 Framely

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

---

## ð Credits & Powered By

### Design Inspiration
- **Netflix** â Card-based history viewer UI patterns
- **Spotify** â Music selector layout and interaction model
- **Apple TV+** â Cinematic typography and dark visual language

### Typography
- [Playfair Display](https://fonts.google.com/specimen/Playfair+Display) by ClÃ©ment Lefebvre â Display headings
- [Inter](https://rsms.me/inter/) by Rasmus Andersson â Body text
- [JetBrains Mono](https://www.jetbrains.com/lp/mono/) by JetBrains â Monospace labels

### AI Infrastructure
- **Story Creator Twin Agent** â AI agent responsible for parsing narratives and generating cinematic video prompts
- **Webhook Pipeline** â Event-driven video generation orchestration

### Open Web Standards
- Built entirely on [W3C Web Standards](https://www.w3.org/standards/) â HTML5, CSS3, ES2022+
- No frameworks harmed in the making of this application ð¬

---

<div align="center">

**ð¬ Framely â Turn your story into cinema.**

*Crafted with obsession for the art of storytelling.*

</div>
