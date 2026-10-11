# Restaurant App

A restaurant mobile app built with **React Native (Expo Router)** and a **Node.js + Express + MongoDB** backend.

- **A1:** frontend with mock data (SRS, UML and screenshots are in the `A1` folder).
- **A2:** REST API, MongoDB database, JWT login, and the app connected to the server (SRS_v2 is in the `A2` folder).

## 1. Project Description

Customers can register, log in, browse and search the menu, manage a cart, use promo codes, place Dine-in or Takeaway orders, track orders and reserve tables.
Managers can manage orders, reservations and menu items (add, edit price, availability, special, delete).
All data is saved in MongoDB, so every phone sees the same menu, orders and reservations.

## 2. Technologies Used

**App:** React Native, Expo, Expo Router, TypeScript / JavaScript, React Hooks, Context API, useReducer, AsyncStorage

**Server:** Node.js, Express, MongoDB (Atlas), Mongoose, JWT (jsonwebtoken), bcryptjs, cors, dotenv

## 3. Main Features

### Customer
- Register / Login (JWT, stays logged in)
- Menu browsing, search and categories
- Food details
- Cart with notes and promo codes (`WELCOME10` = 10%, `FEAST20` = 20%)
- Checkout (Dine-in / Takeaway) and order confirmation
- Order tracking (updates every 10 seconds) and cancel while Pending
- Table reservation (table is assigned automatically)
- Profile, Dark/Light theme, Logout

### Manager
- View all orders and change status (Pending, Preparing, Ready, Served)
- Accept or decline reservations
- Add, edit, delete menu items, edit price
- Availability and special item control
- Dashboard updates every 10 seconds

## 4. Demo Accounts (created by `npm run seed`)

| Role | Email | Password |
| --- | --- | --- |
| Customer | customer@restaurant.com | Customer123 |
| Manager | manager@restaurant.com | Manager123 |

## 5. How to Run

You need Node.js 18+, a MongoDB Atlas connection string, and Expo Go on your phone. The phone and the laptop must be on the **same Wi-Fi**.

### Step 1: Start the backend

```bash
cd server
npm install
```

Copy `.env.example` to `.env` and fill in the values:

```env
PORT=5000
MONGO_URI=mongodb+srv://<username>:<password>@<cluster>.mongodb.net/restaurant_app?appName=Cluster0
JWT_SECRET=any_long_random_text
```

Add demo data to the database (this empties the collections first), then start the server:

```bash
npm run seed
npm run dev
```

You should see `MongoDB connected`. Check it in the browser: `http://localhost:5000/api/health`
(from a phone: `http://<laptop-ip>:5000/api/health`).

### Step 2: Start the app

Open a new terminal in the project root:

```bash
npm install
npx expo start
```

Scan the QR code with Expo Go (or press `w` to open it in the browser).
The app finds the laptop's address from Expo automatically. If it cannot connect, set `LAPTOP_IP` in `src/api/client.js` to your laptop's IP address.

## 6. API Endpoints

Base URL: `http://<laptop-ip>:5000`. Protected routes need the header `Authorization: Bearer <token>`.

| Method | Endpoint | Access |
| --- | --- | --- |
| GET | /api/health | Public |
| POST | /api/auth/register | Public |
| POST | /api/auth/login | Public |
| GET | /api/menu (?category=, ?search=) | Public |
| GET | /api/menu/:id | Public |
| POST | /api/menu | Manager |
| PUT | /api/menu/:id | Manager |
| DELETE | /api/menu/:id | Manager |
| POST | /api/orders | Logged in |
| GET | /api/orders/my | Logged in |
| GET | /api/orders | Manager |
| PATCH | /api/orders/:id/status | Manager (customer: cancel own Pending order) |
| GET | /api/reservations/availability?date=&time= | Logged in |
| POST | /api/reservations | Logged in |
| GET | /api/reservations/my | Logged in |
| GET | /api/reservations | Manager |
| PATCH | /api/reservations/:id | Manager (customer: cancel own booking) |

A Postman collection is in `server/restaurant-api.postman_collection.json`. Import it and run both Login requests first (they save the tokens).

## 7. Database

MongoDB database `restaurant_app` with 5 collections: `users`, `menuitems`, `tables`, `reservations`, `orders`.
Details are in `A2/SRS_v2.pdf` (Section 5).

## 8. Project Structure

```text
RestaurantApp
│
├── A1
│   ├── Screenshots
│   ├── SRS
│   └── UML
│
├── A2
│   └── SRS_v2.pdf
│
├── server
│   ├── config
│   ├── controllers
│   ├── middleware
│   ├── models
│   ├── routes
│   ├── utils
│   ├── app.js
│   ├── server.js
│   ├── seed.js
│   ├── .env.example
│   └── package.json
│
├── assets
├── src
│   ├── api
│   ├── app
│   ├── context
│   ├── hooks
│   ├── reducers
│   └── utils
│
├── app.json
├── package.json
├── README.md
└── tsconfig.json
```

## 9. Demo Video (Q7)

Screen recording (orders, status change, 10-second updates, reservations): **<PASTE LINK HERE>**

## 10. Limitations

- No real online payment
- Updates use polling (every 10 seconds), not push notifications
- The server runs on a laptop only while it is switched on
- Promo codes are fixed in the server code

## 11. Future Enhancements

- Online payment
- Push notifications / real-time updates
- Cloud deployment of the server
- Customer reviews
- Image upload for menu items