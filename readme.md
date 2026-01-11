# 🌍 Zero Hunger Platform

A **full‑stack web platform** designed to reduce food waste and fight hunger by connecting **Donors** (who have surplus food) with **Volunteers** (who pick up and deliver food to people in need). The system ensures transparency, accountability, and motivation through **real‑time tracking** and a **karma‑points based gamification system**.

---

## 🚀 Live Use‑Cases
- Restaurants, events, hostels donate surplus food
- Volunteers pick, deliver, and earn karma points
- Platform tracks impact: food saved, deliveries completed

---

## 🧠 Key Features

### 👤 Donor Module
- Add cooked or packed food items
- Auto‑detect pickup location (GPS)
- Track food status: available → reserved → picked → delivered
- View personal stats (posted, delivered, expired)
- Karma points for successful deliveries

### 🚚 Volunteer Module
- Browse nearby available food
- Pickup cart system
- Pick → Deliver workflow
- Delivery proof (image + address)
- Volunteer portfolio with delivery history
- Karma points & leaderboard ready

### 🌐 Public / Platform
- Welcome page (no login required)
- Platform statistics (total food, deliveries, donors, volunteers)
- Public donor & delivery showcase

---

## 🏗️ System Architecture

```
React + Tailwind CSS (Frontend)
        ↓  REST API
Flask + JWT + Role Guards (Backend)
        ↓
MongoDB Atlas (Database)
```

### 🔐 Security
- JWT Authentication
- Role‑based access control (Donor / Volunteer)
- Secure API routes
- Image handling via Base64 (can be extended to S3/Cloudinary)

---

## 🧩 Tech Stack

### Frontend
- React 18
- Vite
- Tailwind CSS
- Axios
- React Router DOM

### Backend
- Python 3.10+
- Flask
- Flask‑JWT‑Extended
- Flask‑CORS
- MongoDB (PyMongo)

### Database
- MongoDB Atlas

---

## 📦 Required Versions

| Technology | Version |
|----------|---------|
| Node.js | >= 18.x |
| npm | >= 9.x |
| Python | >= 3.10 |
| MongoDB | Atlas / >= 5.x |

---

## 📁 Project Structure

### Frontend (`/frontend`)
```
frontend/
├── src/
│   ├── api/            # Axios API handlers
│   ├── components/     # Reusable UI components
│   ├── pages/
│   │   ├── donor/
│   │   ├── volunteer/
│   │   └── Welcome.jsx
│   ├── routes/
│   ├── assets/
│   └── main.jsx
└── package.json
```

### Backend (`/backend`)
```
backend/
├── app.py
├── config.py
├── models/
│   ├── user_model.py
│   └── food_model.py
├── routes/
│   ├── auth_routes.py
│   └── food_routes.py
├── utils/
│   ├── db.py
│   └── role_required.py
└── requirements.txt
```

---

## 🗃️ Database Schema

### 👤 User Collection
```json
{
  "name": "string",
  "email": "string",
  "password": "hashed",
  "phone": "string",
  "role": "donor | volunteer",
  "address": "string",
  "location": { "lat": number, "lng": number },
  "karmaPoints": number,
  "deliveriesCompleted": number,
  "createdAt": "datetime"
}
```

### 🍱 Food Collection
```json
{
  "foodName": "string",
  "quantity": "string",
  "foodType": "Veg | Non‑Veg",
  "itemCategory": "cooked | packed",
  "expiryTime": "datetime",
  "status": "available | reserved | picked | delivered | expired",
  "donorId": "ObjectId",
  "reservedBy": "ObjectId",
  "deliveryAddress": "string",
  "deliveryImage": "base64",
  "location": { "lat": number, "lng": number },
  "address": "string",
  "createdAt": "datetime"
}
```

---

## 🔄 Food Lifecycle

```
Donor Posts Food
      ↓
Available
      ↓ (Volunteer reserves)
Reserved
      ↓ (Volunteer picks)
Picked
      ↓ (Delivered + Proof)
Delivered (+ Karma)
```

Expired food is automatically marked by background scheduler.

---

## ⭐ Karma Points Logic
- +10 points for every successful delivery
- Stored in user profile
- Used for volunteer portfolio & leaderboard (future)

---

## ⚙️ Installation & Setup

### 1️⃣ Clone Repository
```bash
git clone https://github.com/your-username/zero-hunger-platform.git
cd zero-hunger-platform
```

### 2️⃣ Backend Setup
```bash
cd backend
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt
python app.py
```

Backend runs on: `http://localhost:5000`

---

### 3️⃣ Frontend Setup
```bash
cd frontend
npm install
npm run dev
```

Frontend runs on: `http://localhost:5173`

---

## 🌈 UI/UX Principles Used
- Soft, accessible color palette
- Status‑based color coding
- Micro‑animations & transitions
- Responsive layouts
- Professional dashboards
- Reusable UI components

---

## 📈 Performance Optimizations
- Lazy loading images
- Paginated lists
- Parallel API calls (`Promise.all`)
- Skeleton loaders

---

## 🔮 Future Enhancements
- Google Maps integration
- SMS/WhatsApp notifications
- Leaderboard system
- Admin dashboard
- AI food expiry prediction
- Cloud image storage (S3 / Cloudinary)

---

## 👨‍💻 Author
**Chandra Sekhar Arasavalli**  
B.Tech CSE (2022‑2026)  
Full‑Stack Developer | AI & Systems Enthusiast

---

## 🏁 Conclusion
The **Zero Hunger Platform** is a scalable, real‑world solution addressing food waste and hunger. It combines **modern full‑stack development**, **clean UI/UX**, and **social impact**, making it suitable for **final‑year projects, startups, and NGOs**.

> *"The smallest act of kindness is worth more than the grandest intention."*  

---

© 2026 · Built with ❤️ by **Prograto**

