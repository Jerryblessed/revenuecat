# 🚐 VanBond - Nomadic Dating & Community Platform

**"For God so loved the world, that he gave his only begotten Son..."** - John 3:16

VanBond is a community-driven dating and friendship app designed specifically for van lifers and nomadic individuals. Built with love and purpose, VanBond brings together travelers who share the same passion for the open road while fostering meaningful connections.

---

## ✨ Features

### 🔐 Verified Community
- **Invite-only registration** to maintain a safe, intentional community
- **AI-powered profile verification** using Gemini 3 Flash for authenticity
- Verified badge system for trusted members

### 💕 Nomadic Dating
- **Smart swipe matching** for dating or friendship
- **Distance-based discovery** - find people on similar routes
- **Travel route matching** - connect with nomads heading your way
- Real-time chat with matches

### 🤝 Activity-Based Friends
- Find climbing, hiking, skiing, surfing, and photography buddies
- Filter by activities and interests
- Location-aware recommendations

### 🔧 Builder Hub Marketplace
- Connect with experienced van builders for paid consultations
- **AI Van Build Assistant** powered by Gemini with Google Search
- Book hourly sessions with verified builders
- Get real-time advice on electrical, plumbing, insulation, and more

### 🤖 AI-Powered Features
- **Gemini 3 Flash** for intelligent matching suggestions
- **Google Search integration** for up-to-date van build information
- Activity recommendations based on current location
- Profile verification and safety checks

### 💎 Premium Features (RevenueCat IAP)
- **Free Tier**: 5 discovery credits
- **Pro Plan ($25/month)**: Unlimited swipes, see who likes you, advanced filters, 25 credits
- **Premium Plan ($35/month)**: All Pro features + priority builder access, travel route matching, 50 credits
- **Credit Packs**: Starter (10 credits - $15), Booster (25 credits - $40)

---

## 🛠️ Tech Stack

### Frontend (Flutter)
- **Flutter 3.x** - Cross-platform mobile development
- **Material Design 3** - Modern, beautiful UI
- **State Management** - Provider pattern
- **Networking** - HTTP package for API calls
- **RevenueCat** - In-app purchases & subscriptions
- **Geolocator** - Location services for distance matching
- **Cached Network Image** - Optimized image loading

### Backend (Python/Flask)
- **Flask** - Lightweight REST API
- **SQLite** - Simple, portable database
- **Google Gemini 3 Flash** - AI-powered features
- **Google Search Grounding** - Real-time information retrieval
- **Werkzeug** - Security utilities

---

## 📋 Prerequisites

- **Flutter SDK** 3.0 or higher
- **Python** 3.8 or higher
- **Android Studio** or **Xcode** (for iOS)
- **RevenueCat Account** (for in-app purchases)
- **Google Cloud API Key** (for Gemini AI)

---

## 🚀 Setup Instructions

### Backend Setup (Flask)

1. **Clone the repository**
   ```bash
   cd backend
   ```

2. **Install Python dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Set your Gemini API Key**
   
   Edit `app.py` and replace:
   ```python
   GEMINI_API_KEY = "YOUR_API_KEY_HERE"
   ```
   
   Or use environment variable:
   ```bash
   export GEMINI_API_KEY="your-key-here"
   ```

4. **Initialize the database**
   
   The database will auto-create on first run. Default invite codes:
   - `VANLIFE2025`
   - `NOMAD123`
   - `ROADTRIP`
   - `WANDERLUST`

5. **Run the Flask server**
   ```bash
   python app.py
   ```
   
   Server runs at: `http://localhost:5000`

### Frontend Setup (Flutter)

1. **Update API endpoint**
   
   Edit `main.dart` line 253:
   ```dart
   static const String baseUrl = 'YOUR_SERVER_URL';
   ```
   
   For development:
   - Android Emulator: `http://10.0.2.2:5000`
   - iOS Simulator: `http://localhost:5000`
   - Physical Device: `http://YOUR_IP:5000`

2. **Install Flutter dependencies**
   ```bash
   flutter pub get
   ```

3. **Configure RevenueCat**
   
   Edit `main.dart` line 32:
   ```dart
   await Purchases.configure(
     PurchasesConfiguration('YOUR_REVENUECAT_API_KEY'),
   );
   ```

4. **Update AndroidManifest.xml**
   
   Copy the provided `AndroidManifest.xml` to:
   ```
   android/app/src/main/AndroidManifest.xml
   ```

5. **Run the app**
   ```bash
   flutter run
   ```

---

## 📱 Flutter Package Installation

Run this command to install all required Flutter packages:

```bash
flutter pub add http image_picker cached_network_image intl shared_preferences purchases_flutter geolocator
```

---

## 🗄️ Database Schema

### Users Table
- User authentication and profile data
- Location coordinates for distance matching
- Verification status and tier management

### Swipes & Matches
- Swipe history (left/right)
- Mutual matches tracking
- Match timestamp

### Messages
- Real-time chat between matches
- Read/unread status
- Message history

### Builder Profiles
- Builder expertise and hourly rates
- Session bookings and payments
- Ratings and reviews

### Invite Codes
- Verified community access control
- Tracking code usage

---

## 🎨 UI/UX Design Principles

- **Safety First**: Verified community, invite-only access
- **Location-Aware**: Distance-based matching for travelers
- **Activity-Focused**: Connect over shared adventures
- **Professional**: Builder marketplace for van projects
- **Biblical Values**: Love, generosity, and intentional connection

---

## 🔐 Security Features

1. **Password Hashing** - Werkzeug secure password storage
2. **Invite-Only Registration** - Controlled community growth
3. **AI Profile Verification** - Gemini-powered authenticity checks
4. **Verified Badges** - Trust indicators for community members
5. **Safe Messaging** - Match-only communication

---

## 🤝 Community Values

**"For God so loved the world, that he gave his only begotten Son..."** - John 3:16

Just as connection was meant to be shared, VanBond brings nomads together in:
- **Love** - Finding companionship on the road
- **Generosity** - Sharing knowledge in the Builder Hub
- **Community** - Supporting fellow travelers
- **Purpose** - Intentional, meaningful connections

---

## 🐛 Troubleshooting

### Backend Issues
- **Database locked**: Close all database connections
- **Port 5000 in use**: Change port in `app.py`
- **Gemini API errors**: Check API key validity and quota

### Frontend Issues
- **Network errors**: Verify API endpoint URL
- **RevenueCat errors**: Check API key configuration
- **Location not working**: Enable location permissions in settings
- **Image upload fails**: Check file size limits and permissions

---

## 📊 API Endpoints

### Authentication
- `POST /auth/register` - Register with invite code
- `POST /auth/login` - User login

### Profile Management
- `POST /user/<id>/update` - Update profile
- `POST /user/<id>/upload-image` - Upload profile photo

### Discovery & Matching
- `GET /discover/<id>?mode=dating|friends` - Get potential matches
- `POST /swipe` - Record swipe (left/right)
- `GET /matches/<id>` - Get user's matches

### Messaging
- `GET /messages/<user_id>/<other_id>` - Get conversation
- `POST /messages/send` - Send message

### Builder Hub
- `GET /builders` - List all builders
- `POST /builders/<id>/create` - Create builder profile
- `POST /builders/book` - Book session

### AI Features
- `GET /ai/match-suggestions/<id>` - AI match recommendations
- `POST /ai/van-help` - Ask van build questions
- `GET /ai/activity-recommendations/<id>` - Activity suggestions

---

## 🎯 Roadmap

- [ ] Video chat for matches
- [ ] Group travel events
- [ ] Van build project gallery
- [ ] Route planning integration
- [ ] Offline mode support
- [ ] Push notifications for new matches

---

## 👨‍💻 Development

Built with ❤️ for the nomadic community

### Technologies
- Flutter 3.x
- Flask (Python)
- SQLite
- Google Gemini 3 Flash
- RevenueCat

---

## 📄 License

Copyright © 2025 VanBond. All rights reserved.

---

## 🙏 Acknowledgments

Special thanks to:
- The van life community for inspiration
- RevenueCat for the $20,000 app challenge
- Google Gemini team for amazing AI capabilities
- All nomads living the dream on the road

**"For God so loved the world..."** - Let's share that love through meaningful connections.

---

## 📞 Support

For questions or support:
- Email: support@vanbond.app (example)
- Community Forum: [Coming Soon]
- Bug Reports: GitHub Issues

---

**VanBond** - Where Nomads Connect 🚐💕
