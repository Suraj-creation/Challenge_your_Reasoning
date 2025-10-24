# 🧠 Echo Chamber Buster

**AI-Powered Adversarial Debate Platform**

Challenge your beliefs through relentless, evidence-based debates with an AI that never agrees. Echo Chamber Buster fosters critical thinking and intellectual humility by immersing you in philosophical sparring backed by historical wisdom, spiritual texts, and scientific research.

![Version](https://img.shields.io/badge/version-1.0.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Status](https://img.shields.io/badge/status-production--ready-brightgreen)

---

## 🎯 Purpose

Break free from confirmation bias. This application takes an adversarial stance on controversial topics across 8 domains—from free will to climate policy—forcing you to defend your positions against rigorous counterarguments. The AI, powered by Google Gemini, cites philosophers like Socrates and Nietzsche, spiritual texts like the Bhagavad Gita, and peer-reviewed research to dismantle your reasoning.

**Core Philosophy**: "No truth is absolute—flaws lurk in every certainty."

---

## ✨ Features

### 🔥 **Adversarial AI Debates**
- **40+ Controversial Topics** across 8 domains:
  - Life & Existence • Ethics & Morality • Rights & Justice
  - Traditions & Culture • Society & Politics • Science & Philosophy
  - Psychology & Behavior • Environment & Technology
- **Never Agrees**: AI always opposes your position
- **Evidence-Based**: Cites philosophers, spiritual texts, scientific research

### 📚 **Authoritative Sources**
- **Great Thinkers**: Socrates, Nietzsche, MLK Jr., Gandhi, Einstein, Freud, Marcus Aurelius, Seneca
- **Spiritual Texts**: Bhagavad Gita, Bible, Quran, Tao Te Ching, Upanishads
- **Research**: Kahneman, Milgram, WHO, IPCC, peer-reviewed studies

### 🎓 **Intellectual Humility**
- Every 3rd AI response includes: *"Remember, no truth is absolute—flaws lurk in every certainty."*
- Surrender detection with encouraging wrap-ups

### 💾 **Session Management**
- Fresh topic generation on each new visit
- Conversation history (last 5 debates)
- Session persistence across refreshes

### 🎨 **Modern UI/UX**
- ChatGPT-inspired interface
- Light/Dark theme toggle with persistence
- Fully responsive (mobile, tablet, desktop)
- Smooth animations and typing indicators

### 🔄 **Robust Error Handling**
- Exponential backoff retry (1s, 2s, 4s)
- Specific rate limit (429) handling
- Graceful fallback responses
- Detailed console logging for debugging

---

## 🚀 Quick Start

### **Installation**
No installation required! Simply:

1. **Download** `index.html`
2. **Open** in a modern browser (Chrome 90+, Firefox 88+, Safari 14+, Edge 90+)
3. **Start debating!**

### **Requirements**
- Modern web browser with JavaScript enabled
- Internet connection (for Gemini API calls)

---

## 🛠️ Technology Stack

- **Frontend**: Pure HTML5, CSS3, JavaScript ES6+
- **AI**: Google Gemini API (gemini-1.5-flash model)
- **Architecture**: Single-file self-contained application
- **No Dependencies**: Zero external libraries or frameworks

**Why Single-File?**
- ✅ Instant deployment (GitHub Pages, Vercel, Netlify)
- ✅ No build process or bundler required
- ✅ Works on `file://` protocol
- ✅ Easy to inspect, modify, and understand

---

## 📖 Usage Guide

### **Starting a Debate**
1. A controversial topic generates automatically on first visit
2. Type your perspective in the input box
3. Press **Enter** or click **Send**
4. AI responds with counterarguments backed by sources

### **Surrender Detection**
Type phrases like:
- "I give up"
- "You're right"
- "Enough"
- "I surrender"

The AI will acknowledge your intellectual humility with an encouraging message.

### **New Debate**
Click the **"New Debate"** button in the sidebar to:
- Generate a fresh controversial topic
- Clear current conversation
- Start a new philosophical sparring session

### **Theme Toggle**
Click **Dark Mode / Light Mode** button to switch themes. Preference persists across sessions.

### **Conversation History**
- Last 5 debates are saved in **"Recent Debates"**
- Click any history item to review that conversation

---

## 🏗️ Architecture

### **EchoChamberBuster Class**
Main application controller managing:
- API integration with exponential backoff
- UI rendering and state management
- Session/localStorage persistence
- Error handling and retry logic

### **Prompt Engineering**
Dynamic adversarial prompts enforce 4-part structure:
1. **Acknowledge & Question**: Empathy + Socratic questioning
2. **Core Counter**: Main counterargument
3. **Evidence Montage**: 2+ authoritative sources
4. **Closing**: Thought-provoking question

### **State Management**
- **sessionStorage**: Current conversation (resets per browser session)
- **localStorage**: Last 5 debate histories + theme preference
- **In-memory**: Full conversation array for API context window

---

## ⚙️ Configuration

### **API Key Setup**
1. Get a free API key from [Google AI Studio](https://aistudio.google.com/app/apikey)
2. Replace the key on **line 715** in `index.html`:
   ```javascript
   this.apiKey = 'YOUR_API_KEY_HERE';
   ```
3. **⚠️ Production Warning**: Never expose API keys client-side. Use a backend proxy in production.

### **Customizing Topics**
Edit the `controversialTopics` object (line ~660) to add/modify topics:
```javascript
this.controversialTopics = {
    lifeExistence: [
        "Your custom controversial question here?",
        // Add more...
    ],
    // Add new domains...
};
```

### **Adjusting AI Parameters**
Modify `generationConfig` (line ~1030):
```javascript
generationConfig: {
    temperature: 0.9,      // Creativity (0.0-1.0)
    topK: 40,              // Token sampling
    topP: 0.95,            // Nucleus sampling
    maxOutputTokens: 800   // Response length
}
```

### **Theme Customization**
Edit CSS variables (line ~95):
```css
:root {
    --sidebar-bg: #202123;
    --main-bg: #343541;
    --user-message-bg: #10A37F;
    /* Customize colors here */
}
```

---

## 🔒 Security & Privacy

### **Client-Side API Key**
⚠️ **Current Implementation**: API key is embedded for demo purposes only.

**Production Recommendations**:
1. Create a backend proxy server (Node.js, Python Flask, etc.)
2. Move API key to server-side environment variables
3. Frontend calls your proxy, not Gemini directly
4. Implement rate limiting on your proxy

### **Content Security Policy (CSP)**
CSP meta tag restricts resource loading:
- Scripts: `'self'` + `'unsafe-inline'` (required for embedded JS)
- Styles: `'self'` + `'unsafe-inline'` (required for embedded CSS)
- Connections: `https://generativelanguage.googleapis.com` only
- Images: `'self'` + `data:` URIs

### **Privacy**
- ✅ No user tracking or analytics
- ✅ No personal data collection
- ✅ Data stored only in browser (localStorage/sessionStorage)
- ✅ Anonymous API calls (no user identification)

---

## 🧪 Testing

### **Automated Tests**
Use `test-api.html` (included) to verify API connection:
```bash
# Open in browser
open test-api.html
```

### **Manual Testing Checklist**
- [ ] Topic loads automatically on first visit
- [ ] AI provides counter-arguments with sources
- [ ] Every 3rd response includes humility reminder
- [ ] Surrender phrases trigger graceful exit
- [ ] "New Debate" generates fresh topic
- [ ] Theme toggle persists on reload
- [ ] Conversation history stores last 5 debates
- [ ] Mobile hamburger menu works (<768px)
- [ ] Retry logic handles connection failures
- [ ] Console logs show API responses (F12)

### **Browser Compatibility**
| Browser | Version | Status |
|---------|---------|--------|
| Chrome  | 90+     | ✅ Full Support |
| Firefox | 88+     | ✅ Full Support |
| Safari  | 14+     | ✅ Full Support |
| Edge    | 90+     | ✅ Full Support |

---

## 📦 Deployment

### **GitHub Pages**
1. Create a GitHub repository
2. Upload `index.html` to root
3. Enable GitHub Pages in Settings → Pages
4. Access at `https://yourusername.github.io/repo-name/`

### **Vercel**
```bash
# Install Vercel CLI
npm i -g vercel

# Deploy
vercel --prod
```

### **Netlify**
1. Drag `index.html` to [Netlify Drop](https://app.netlify.com/drop)
2. Or connect GitHub repo for auto-deployment

### **Custom Domain**
All platforms support custom domains. See provider docs for DNS configuration.

---

## 🐛 Troubleshooting

### **API Key Issues**
- **Error 401/403**: Invalid API key or restrictions
  - Verify key at [Google AI Studio](https://aistudio.google.com/app/apikey)
  - Check for domain restrictions (should be none for testing)
  - Ensure key is enabled

### **Rate Limiting (429)**
- **Solution**: App implements automatic exponential backoff
- If persistent: Wait 5 minutes or create new API key

### **Content Blocked (400)**
- **Cause**: Safety filters triggered
- **Solution**: Rephrase your message or try different topic

### **No Response Generated**
- **Check**: Browser console (F12) for detailed error logs
- **Look for**: "Gemini API Error" or "Gemini API Response"
- **Verify**: Internet connection active

---

## 🗺️ Roadmap

### **Planned Features**
- [ ] 🎤 Voice input support (mic icon ready)
- [ ] 🌍 Multi-language debates
- [ ] 📝 Custom topic submission
- [ ] 📊 Debate analytics (argument strength, source diversity)
- [ ] 💾 Export conversations (PDF, Markdown)
- [ ] 🤝 Two-player mode (debate against another human)
- [ ] 🧩 Browser extension version

### **Advanced Enhancements**
- [ ] Token counting for context window optimization
- [ ] Streaming responses (real-time typing)
- [ ] Alternative AI models (Claude, GPT-4)
- [ ] Argument visualization (mind maps)

---

## 🤝 Contributing

Contributions welcome! Here's how:

1. **Fork** the repository
2. **Create** a feature branch: `git checkout -b feature/amazing-feature`
3. **Commit** changes: `git commit -m 'Add amazing feature'`
4. **Push** to branch: `git push origin feature/amazing-feature`
5. **Open** a Pull Request

### **Code Style**
- ES6+ JavaScript
- Semantic HTML5
- BEM-like CSS naming
- JSDoc comments for methods
- Inline comments for complex logic

### **Bug Reports**
Open an issue with:
- Browser/OS version
- Steps to reproduce
- Expected vs actual behavior
- Console logs (F12)

---

## 📜 License

**MIT License**

Permission is hereby granted, free of charge, to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of this software. See [LICENSE](LICENSE) for full terms.

---

## 🙏 Credits

### **Powered By**
- [Google Gemini API](https://ai.google.dev/) - AI responses
- Inspired by [ChatGPT](https://chat.openai.com/) interface design

### **Philosophical Foundation**
Built on the principle that intellectual humility—acknowledging the limits of our certainty—is the foundation of genuine learning. Inspired by:
- **Socrates**: "I know that I know nothing"
- **Nietzsche**: Questioning absolute truths
- **Bhagavad Gita**: Detachment from rigid views

### **Open Source**
This project stands on the shoulders of open web standards and the vibrant developer community.

---

## 📧 Contact & Support

- **Issues**: [GitHub Issues](https://github.com/yourusername/echo-chamber-buster/issues)
- **Discussions**: [GitHub Discussions](https://github.com/yourusername/echo-chamber-buster/discussions)
- **Email**: your.email@example.com

---

## ⚖️ Disclaimer

This app challenges ideas, not people. Debates are simulations designed to provoke critical thinking. The AI's positions do not reflect the views of the developers or Google. Always seek diverse perspectives in real life and approach controversial topics with empathy and nuance.

---

<div align="center">

**Built with 🧠 for those who dare to question everything**

[⭐ Star on GitHub](https://github.com/yourusername/echo-chamber-buster) • [🐛 Report Bug](https://github.com/yourusername/echo-chamber-buster/issues) • [💡 Request Feature](https://github.com/yourusername/echo-chamber-buster/discussions)

</div>
