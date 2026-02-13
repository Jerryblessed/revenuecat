# AI Coach - Democratizing Personal Coaching

**Guidance at the right moment changes everything.**

AI Coach is a beautiful, minimal mobile app that makes personal coaching accessible to everyone through AI. Browse, create, and share AI coaches, add your personal context, and start getting meaningful guidance immediately.

---

## 🌟 Features

### Core Features
- **Discover Coaches**: Browse a marketplace of AI coaches for productivity, career, wellness, and more
- **Create Custom Coaches**: Design your own AI coaches with specific expertise and coaching styles
- **Personal Context**: Add your background and values for personalized coaching
- **Real-time Chat**: Engage in natural conversations with AI coaches powered by Gemini 3
- **Share Coaches**: Share your custom coaches with the community

### AI Capabilities (Powered by Gemini 3)
- **Deep Thinking**: Coaches use Gemini 3's reasoning for thoughtful, well-considered responses
- **Search Grounding**: Real-time information from Google Search for factual accuracy
- **Structured Outputs**: Consistent, high-quality coaching interactions
- **Context-Aware**: Coaches remember your personal context across conversations

### Monetization (RevenueCat)
- **Free Tier**: 5 trial credits to explore
- **Pro Plan ($25/month)**: 11 coach creations, 50 chat sessions
- **Premium Plan ($35/month)**: 20 coach creations, 100 chat sessions
- **Credit Packs**: One-time purchases (10 credits for $15, 25 credits for $40)

---

## 🏗️ Architecture

### Frontend (Flutter)
- **Clean Material 3 Design**: Minimalist UI focused on productivity
- **State Management**: Simple state with SharedPreferences
- **Navigation**: Bottom navigation with 5 main screens
- **Network**: HTTP client for REST API communication
- **Payments**: RevenueCat for in-app purchases and subscriptions

### Backend (Flask + Python)
- **Database**: SQLite for user data, coaches, and conversations
- **AI Integration**: Google Gemini 3 Flash with thinking and search grounding
- **Authentication**: Email/password with secure hashing
- **RESTful API**: Clean endpoints for all operations

### AI Features
- **Dynamic Coach Creation**: Gemini 3 generates system prompts based on expertise
- **Context-Aware Coaching**: User context and values inform all interactions
- **Search-Enhanced**: Coaches can access real-time information via Google Search
- **Thinking Mode**: High-level reasoning for complex coaching scenarios

---

## 🚀 Setup Instructions

### Prerequisites
- Flutter SDK (3.0+)
- Python 3.8+
- Android Studio or Xcode
- Google Gemini API Key

### Backend Setup

1. **Install Python Dependencies**
```bash
pip install -r requirements.txt
```

2. **Configure API Key**
Edit `app.py` and add your Gemini API key:
```python
GEMINI_API_KEY = "your_api_key_here"
```

3. **Run the Backend**
```bash
python app.py
```

The server will start on `http://localhost:5000`

### Frontend Setup

1. **Install Flutter Dependencies**
```bash
flutter pub get
```

2. **Update Base URL**
Edit `main.dart` and update the API base URL:
```dart
static const String baseUrl = 'http://YOUR_IP:5000';
```

For Android Emulator: Use `http://10.0.2.2:5000`  
For iOS Simulator: Use `http://localhost:5000`  
For Physical Device: Use your computer's local IP

3. **Configure RevenueCat**
Replace the API key in `main.dart`:
```dart
await Purchases.configure(
  PurchasesConfiguration('YOUR_REVENUECAT_API_KEY'),
);
```

4. **Run the App**
```bash
flutter run
```

---

## 📱 App Structure

### Main Screens

1. **Discover**: Browse and search public AI coaches
2. **My Coaches**: View and manage your created coaches
3. **Context**: Set your personal background and values
4. **Upgrade**: Purchase subscriptions and credit packs
5. **Settings**: Profile, credits overview, and logout

### User Flow

```
Login/Register
    ↓
Discover Coaches → Select Coach → Start Chat
    ↓                    ↓
My Coaches ←    Create New Coach
    ↓
Add Context & Values
    ↓
Enhanced Coaching Experience
```

---

## 🎨 Design Principles

- **Minimal**: Clean, focused interface without clutter
- **Productive**: Quick access to coaches and conversations
- **Beautiful**: Material 3 design with thoughtful color scheme (Indigo primary)
- **Accessible**: Clear typography, proper contrast, intuitive navigation

---

## 🤖 Gemini 3 Integration Details

### Coach Creation
- Uses Gemini 3 Flash with medium thinking
- Generates comprehensive system prompts
- Incorporates user context and values
- Returns structured, actionable coaching guidelines

### Chat Conversations
- Uses Gemini 3 Flash with high thinking for deep reasoning
- Search grounding enabled for factual questions
- Maintains conversation history with thought signatures
- Personalized with user context

### Features Used
- ✅ Thinking (high level for coaching)
- ✅ Search Grounding (for real-time information)
- ✅ Structured Outputs (for coach creation)
- ✅ System Instructions (for coach personalities)
- ✅ Context Window (1M tokens for long conversations)

---

## 💾 Database Schema

### Users Table
- id, email, password (hashed)
- trials, tier, coach_creation_credits, chat_credits
- context_text, values_text
- created_at

### Coaches Table
- id, name, description, expertise
- system_prompt (AI-generated)
- creator_id, is_public, share_count
- created_at

### Conversations Table
- id, user_id, coach_id
- messages (JSON array)
- created_at, updated_at

---

## 🔒 Security

- Passwords hashed with Werkzeug's PBKDF2
- Session stored locally with SharedPreferences
- API key stored server-side only
- CORS enabled for cross-origin requests
- User context private and encrypted

---

## 📊 Monetization Strategy

### Free Tier
- 5 trial credits
- Access to public coaches
- Limited chat sessions

### Pro Tier ($25/month)
- 11 coach creations per month
- 50 chat sessions
- Priority support

### Premium Tier ($35/month)
- 20 coach creations per month
- 100 chat sessions
- Unlimited analysis
- Early access to new features

### Credit Packs (One-time)
- Starter Pack: 10 credits for $15
- Power Pack: 25 credits for $40

---

## 🛠️ Development

### Adding New Coaches (Default)
Edit `seed_default_coaches()` in `app.py`:
```python
{
    'name': 'Your Coach Name',
    'expertise': 'Your Expertise Area',
    'description': 'What this coach helps with',
}
```

### Customizing AI Behavior
Adjust thinking levels in chat endpoint:
```python
thinking_config=types.ThinkingConfig(thinking_level="high")
```

### UI Customization
Update color scheme in `main.dart`:
```dart
colorScheme: ColorScheme.fromSeed(
  seedColor: const Color(0xFF6366F1), // Indigo
  brightness: Brightness.light,
)
```

---

## 🐛 Troubleshooting

### Backend Issues
- **Database locked**: Close other connections to `aicoach.db`
- **API key error**: Verify Gemini API key is correct
- **Port in use**: Change port in `app.run()`

### Frontend Issues
- **Network error**: Check backend is running and URL is correct
- **RevenueCat error**: Verify API key and product IDs
- **Build fails**: Run `flutter clean` then `flutter pub get`

---

## 📈 Roadmap

- [ ] Voice coaching sessions
- [ ] Coach analytics and insights
- [ ] Team/group coaching
- [ ] Integration with calendar/tasks
- [ ] Web version
- [ ] Coach ratings and reviews

---

## 🤝 Contributing

This app was built for the Simon's AI Coaching App Competition. Feel free to extend and improve it!

---

## 📄 License

MIT License - Built with ❤️ using Flutter, Flask, and Gemini 3

---

## 🙏 Acknowledgments

- **Simon**: For the vision of democratizing coaching
- **Google Gemini**: For powerful AI capabilities
- **RevenueCat**: For seamless in-app purchases
- **Flutter Team**: For amazing cross-platform framework

---

**The right guidance at the right moment can change everything. Start your coaching journey today!**
