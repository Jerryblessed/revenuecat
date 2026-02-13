# PortfolioMaster 📊💰

**Your AI-Powered Investment Portfolio Tracking Companion**

PortfolioMaster is a comprehensive investment portfolio management app that helps investors track all their assets across multiple platforms in one place. Powered by Google's Gemini 3 Flash AI, it provides real-time price updates, risk analysis, and intelligent diversification recommendations.

---

## 🌟 Features

### Core Features (All Tiers)
- ✅ **Multi-Asset Support**: Track stocks, crypto, gold, real estate, fixed income, funds, and more
- ✅ **Cross-Platform Tracking**: Consolidate investments from XTB, Renta Quattro, and other platforms
- ✅ **Manual Entry**: Add non-listed assets like real estate or fixed income products
- ✅ **Portfolio Overview**: Visual dashboard with total value and profit/loss tracking
- ✅ **Maturity Alerts**: Set reminders for fixed income maturity dates

### Premium Features (Pro & Premium Tiers)
- 🤖 **AI-Powered Analysis**: Deep portfolio analysis using Gemini 3 Flash
- 📊 **Risk Assessment**: Understand your portfolio's risk profile
- 🌍 **Country Exposure**: See your geographical diversification
- 🏭 **Sector Exposure**: Track industry concentration
- 💡 **Smart Recommendations**: Get AI-generated suggestions to improve diversification
- 📈 **Real-Time Price Updates**: Automatic price fetching for listed assets using Google Search grounding

---

## 🏗️ Architecture

### Frontend (Flutter)
- **Framework**: Flutter 3.x with Material Design 3
- **State Management**: Provider pattern with StatefulWidgets
- **Charts**: fl_chart for beautiful data visualization
- **Payments**: RevenueCat for in-app purchases
- **Notifications**: flutter_local_notifications with timezone support

### Backend (Python Flask)
- **Framework**: Flask 3.0 with CORS support
- **Database**: SQLite for lightweight, portable data storage
- **AI Engine**: Google Gemini 3 Flash via genai SDK
- **Authentication**: Email/password + Google OAuth support

### AI Integration
- **Model**: gemini-3-flash-preview
- **Capabilities**:
  - Real-time price fetching with Google Search grounding
  - Portfolio risk analysis with high-level thinking
  - Code execution for complex calculations
  - Structured JSON outputs for consistent responses

---

## 📦 Installation

### Prerequisites
- Flutter SDK 3.16.0 or higher
- Python 3.10 or higher
- Android Studio / Xcode for mobile deployment
- Google Gemini API key

### Backend Setup

1. **Install Python dependencies**:
```bash
pip install -r requirements.txt
```

2. **Set up environment variables**:
   - Replace the API key in `app.py` with your Gemini API key:
   ```python
   GEMINI_API_KEY = "your_gemini_api_key_here"
   ```

3. **Run the Flask server**:
```bash
python app.py
```

The server will start on `http://0.0.0.0:5000`

### Frontend Setup

1. **Install Flutter dependencies**:
```bash
flutter pub get
```

2. **Update API endpoint** (if needed):
   In `main.dart`, update the `baseUrl` in `ApiService`:
   ```dart
   static const String baseUrl = 'your_backend_url_here';
   ```

3. **Configure RevenueCat**:
   - Replace the RevenueCat API key in `main.dart`:
   ```dart
   await Purchases.configure(
     PurchasesConfiguration('your_revenuecat_key_here'),
   );
   ```

4. **Run the app**:
```bash
# For Android
flutter run

# For iOS
flutter run -d ios

# For web
flutter run -d chrome
```

---

## 🚀 Quick Start Guide

### Adding Your First Investment

1. **Navigate to Investments Tab** → Tap the floating "Add Investment" button
2. **Select Asset Type**: Stock, Crypto, Gold, Real Estate, etc.
3. **Enter Details**:
   - Asset name (e.g., "AAPL", "Bitcoin")
   - Quantity
   - Purchase price
   - Current price (or tap search icon for AI-powered price fetch)
4. **Optional Info**: Platform, country, sector, maturity date
5. **Save** → Your investment is now tracked!

### Getting AI Analysis

1. **Navigate to Analytics Tab**
2. **Tap "Analyze Portfolio"**
3. **Wait for AI Processing** (Gemini 3 Flash with high-level thinking)
4. **View Results**:
   - Overall risk level
   - Country exposure breakdown
   - Sector concentration
   - Personalized recommendations

### Updating Prices

1. **Go to Portfolio Tab**
2. **Tap the refresh icon** in the app bar
3. **AI automatically fetches current prices** for all listed assets (stocks, crypto, gold)

---

## 💳 Pricing Tiers

| Feature | Free | Pro ($25/mo) | Premium ($35/mo) |
|---------|------|--------------|------------------|
| Track Investments | ✅ Unlimited | ✅ Unlimited | ✅ Unlimited |
| Manual Price Entry | ✅ Yes | ✅ Yes | ✅ Yes |
| Real-time Price Updates | ❌ No | ✅ Yes | ✅ Yes |
| AI Portfolio Analysis | 5 trials | 50/month | ♾️ Unlimited |
| Risk Assessment | ❌ No | ✅ Yes | ✅ Yes |
| Diversification Insights | ❌ No | ✅ Yes | ✅ Yes |
| Custom Alerts | ❌ No | ❌ No | ✅ Yes |
| Priority Support | ❌ No | ✅ Yes | ✅ Premium |

### One-Time Credit Packs
- **Starter Pack**: 10 analyses for $15
- **Investor Pack**: 25 analyses for $40

---

## 🔧 Technical Details

### Database Schema

**Users Table**:
```sql
CREATE TABLE users (
    id INTEGER PRIMARY KEY,
    email TEXT UNIQUE,
    password TEXT,
    trials_remaining INTEGER DEFAULT 5,
    analysis_credits INTEGER DEFAULT 0,
    tier TEXT DEFAULT 'free',
    alerts_enabled INTEGER DEFAULT 1
)
```

**Investments Table**:
```sql
CREATE TABLE investments (
    id TEXT PRIMARY KEY,
    user_id INTEGER,
    name TEXT,
    type TEXT,
    quantity REAL,
    purchase_price REAL,
    current_price REAL,
    currency TEXT DEFAULT 'USD',
    purchase_date TEXT,
    platform TEXT,
    country TEXT,
    sector TEXT,
    maturity_date TEXT,
    notes TEXT,
    created_at TEXT,
    FOREIGN KEY(user_id) REFERENCES users(id)
)
```

### API Endpoints

#### Authentication
- `POST /auth/register` - Register new user
- `POST /auth/login` - Email/password login
- `POST /auth/google` - Google OAuth login

#### Investments
- `GET /api/investments/<user_id>` - Get all investments
- `POST /api/investments` - Add new investment
- `PUT /api/investments/<investment_id>` - Update investment
- `DELETE /api/investments/<investment_id>` - Delete investment

#### AI Features
- `POST /api/get-price` - Fetch real-time price for an asset
- `POST /api/update-prices` - Update all investment prices
- `POST /api/analyze-portfolio` - AI-powered portfolio analysis

---

## 🧠 AI Features Explained

### Price Fetching
Uses Gemini 3 Flash with **Google Search grounding** to fetch real-time prices:
```python
response = client.models.generate_content(
    model="gemini-3-flash-preview",
    contents=f"Current price of {asset_name} in USD",
    config=types.GenerateContentConfig(
        tools=[{"google_search": {}}],
        thinking_config=types.ThinkingConfig(thinking_level="low")
    )
)
```

### Portfolio Analysis
Uses **high-level thinking** for deep analysis with **code execution** for complex calculations:
```python
response = client.models.generate_content(
    model="gemini-3-flash-preview",
    contents=analysis_prompt,
    config=types.GenerateContentConfig(
        thinking_config=types.ThinkingConfig(thinking_level="high"),
        response_mime_type="application/json",
        tools=[types.Tool(code_execution=types.ToolCodeExecution())]
    )
)
```

---

## 📱 App Screenshots

*(Add screenshots here)*

---

## 🛣️ Roadmap

- [ ] Import portfolio from CSV/Excel
- [ ] Multi-currency support
- [ ] Portfolio comparison with benchmarks
- [ ] Tax loss harvesting suggestions
- [ ] Desktop app (Windows/Mac/Linux)
- [ ] Social features - share portfolio allocations
- [ ] Integration with brokerage APIs (Alpaca, Interactive Brokers)

---

## 🤝 Contributing

We welcome contributions! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

---

## 🙏 Acknowledgments

- **Google Gemini Team** for the powerful AI capabilities
- **RevenueCat** for seamless in-app purchase management
- **Flutter Team** for the amazing cross-platform framework
- **All contributors** who helped make this project better

---

## 📞 Support

- **Email**: support@portfoliomaster.app
- **Discord**: [Join our community](https://discord.gg/portfoliomaster)
- **Documentation**: [Full docs](https://docs.portfoliomaster.app)

---

## ⚠️ Disclaimer

PortfolioMaster is a portfolio tracking tool and does NOT provide financial advice. All investment decisions should be made after consulting with qualified financial advisors. Past performance does not guarantee future results. Invest responsibly.

---

**Made with ❤️ by developers who love investing**
