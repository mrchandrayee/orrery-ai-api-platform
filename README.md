# Orrery — AI API Platform Dashboard

[![Live Demo](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-blue?style=for-the-badge&logo=github)](https://mrchandrayee.github.io/orrery-ai-api-platform/)
[![HTML](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org) [![CSS](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)](https://developer.mozilla.org) [![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](./LICENSE)

Responsive, runnable frontend recreation based on the supplied 14.43-second screen recording.

## Run locally
1. Extract `orrery-ai-api-platform.zip`.
2. Open `index.html` in a modern browser.

No npm install, bundler or build command is needed.

Optional local server:
```bash
python3 -m http.server 8000
```
Then visit `http://localhost:8000`.

## Screens recreated from the video

Brand / workspace shown: **Orrery**, **Northwind Labs**, Scale plan · us-east. The dashboard greeting is **Good afternoon, Nadia**.

### Overview
- Requests today: 118.3k
- Tokens today: 303.15M
- Spend this month: $9,846; forecast $12,957
- Median latency: 697ms
- Requests-per-hour chart and live indicator
- Model status list: Atlas 3, Atlas 3 Mini, Lyra Vision, Echo Embed
- Recent request table and spend-by-model chart
- Open Playground and Create key actions

### Playground
- System prompt and user message editor
- Model selector: Atlas 3, Atlas 3 Mini, Lyra Vision, Echo Embed
- Run button with simulated streamed response
- Response copy, generated JS example
- Temperature, max output tokens and Top P controls
- Visible prompt in the recording: customer on Starter plan asks why their invoice went up; draft a short, friendly reply.

### Logs
- All / Success / Errors filters
- Model and API-key filters, request search
- Request rows with time, status, model, key, endpoint, tokens, latency and cost
- Pause / resume live view and CSV export

### Usage
- 7 days / 30 days / 90 days periods
- Spend / Tokens / Requests tabs
- Summary metrics and stacked daily usage chart

### Models
- Atlas 3, Atlas 3 Mini, Lyra Vision and Echo Embed
- Text / Vision / Embeddings filters
- Model descriptions, context, pricing, latency and status
- Try it action opens the Playground with that model selected

### API keys
- Sample key list with environment and last-used labels
- Create and revoke key interactions

### Organisation
- Billing: Scale plan, $18,000 monthly budget, $9,846 spent, forecast and payment-method panel
- Team: workspace members and invite action
- Settings: workspace preferences and toggle controls
- Docs: quickstart, API reference, SDKs, authentication, usage and status guide cards

Also includes responsive layout, collapsible sidebar, dark mode, global search shortcut (Ctrl/⌘ + K), modal forms, toasts and CSV exports.

## Readable code fragment visible in the video

The code editor is labelled `playground.js` and shows a streaming `step` function. The readable logic is:

```js
const step = () => {
  // A couple of words per frame of output, at the model's speed.
  let chunk = '', t = 0;
  while (i < words.length && t < 3) {
    const w = words[i++];
    chunk += w + ' ';
    if (w.trim()) {
      const n = tokOf(w);
      t += n;
      inTok += n;
      outTok += n;
    }
  }
  caret.before(document.createTextNode(chunk));
  if (outTok >= limit) return finish(limit, 'max_tokens', ttft);
  if (i >= words.length) return finish(finishTok, 'end_turn', ttft);
  running = gsap.delayedCall(perTok, step);
};
running = gsap.delayedCall(ttft / 1000, () => {
  stat('ttft', ms(ttft));
  step();
});
```

The video exposes this small JavaScript fragment, not the full original application source. The project implements the same visible dashboard concepts and a frontend-only response streaming simulation; the unseen original source cannot be extracted from the recording.

## Demo / backend limitations
- Dashboard metrics, models, logs, keys, billing and team data are local sample data based on visible labels and figures.
- Playground responses are simulated locally; no LLM provider is called.
- API key creation/revocation, billing, invites, settings and logs are demo interactions only.
- No authentication, API gateway, database, usage metering, payment processing or production security is included.
- Do not use demo keys or billing forms for real services.

## 👨‍💻 Author

**mrchandrayee** · [GitHub](https://github.com/mrchandrayee)

## 📄 License

[MIT License](./LICENSE)
