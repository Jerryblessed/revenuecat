# MumWise 💰

**AI-powered financial guidance for busy mums seeking independence**

---

## 💡 Inspiration

Busy mums constantly struggle with financial decisions while juggling family responsibilities. They need quick, practical money advice but lack time for lengthy research. MumWise was born from recognizing this gap - giving mums instant access to AI-powered financial wisdom tailored to their everyday lives.

## 🎯 What it does

MumWise is your pocket financial advisor that helps you:
- Find cheaper shopping alternatives instantly
- Calculate batch cooking savings vs takeout
- Get DIY renovation tips to save thousands
- Learn investment basics without overwhelm  
- Receive personalized money-saving advice via AI chat
- Track expenses and savings goals

## 🛠️ How we built it

**Tech Stack:**
- **Frontend:** Flutter (cross-platform mobile)
- **Backend:** Python Flask with SQLite
- **AI:** Google Gemini 3 Flash with Search grounding
- **Monetization:** RevenueCat for subscriptions
- **UI:** Material Design 3 with custom financial theme

**Key Features:**
- Gemini 3 Flash provides instant, intelligent responses
- Google Search grounding ensures current pricing data
- Response caching (24hr) reduces costs
- Dynamic thinking levels optimize AI performance

## 🚧 Challenges we ran into

- **Prompt Engineering:** Crafting prompts that give practical, actionable advice instead of generic responses
- **Cost Optimization:** Implementing smart caching to reduce API calls while maintaining freshness
- **UX Balance:** Making financial advice approachable without oversimplifying complex topics
- **Real-time Pricing:** Ensuring shopping alternatives reflect current market prices via search grounding

## 🏆 Accomplishments that we're proud of

✅ Built a complete AI financial advisor in one cohesive app  
✅ Integrated Gemini 3 Flash with Google Search for accurate, current data  
✅ Created an intuitive UI that makes finance feel friendly, not intimidating  
✅ Implemented smart caching that cuts API costs by ~60%  
✅ Designed a sustainable monetization model accessible to all income levels

## 📚 What we learned

- **AI is powerful but needs direction:** Generic prompts give generic answers. Specific, context-rich prompts unlock real value
- **Speed matters:** Gemini 3 Flash's low latency makes the AI feel conversational, not robotic
- **Caching is crucial:** Smart response caching dramatically reduces costs while maintaining user experience
- **Financial advice needs empathy:** The tone and framing matter as much as the content

## 🚀 What's next for MumWise

**Short-term:**
- Receipt scanning with OCR for expense tracking
- Budget planner with AI recommendations
- Community forum for sharing money-saving tips

**Long-term:**
- Bank account integration (read-only) for automated expense tracking
- Investment portfolio tracking with AI insights
- Meal planning with cost optimization
- Partnership with financial institutions for exclusive deals

---

## 💳 Pricing

**Subscriptions:**
- Pro: $6/month (₦10,000) - 11 credits each for advice & analysis
- Premium: $12/month (₦20,000) - 20 credits + unlimited features

**Top-ups:**
- 10 Credits: $5 (₦8,000)
- 25 Credits: $6 (₦9,500)

---

## 🚀 Quick Start

```bash
# Install Flutter dependencies
flutter pub add http cached_network_image intl shared_preferences purchases_flutter flutter_local_notifications google_sign_in timezone image_picker file_picker fl_chart

# Install Python dependencies
pip install -r requirements.txt

# Set Gemini API key
export GEMINI_API_KEY="your_key_here"

# Run backend
python app.py

# Run app
flutter run
```

---

**Built with ❤️ for financial freedom**
