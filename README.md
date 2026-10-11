# Restaurant App MVP

## 1. Project Description

Restaurant App MVP is a frontend-only mobile application developed using React Native and Expo Router.

It allows customers to browse food, search menu items, manage their cart, place mock orders, track orders, and reserve tables.

Managers can manage orders, reservations, and menu items.

## 2. Technologies Used

- React Native
- Expo
- Expo Router
- TypeScript / JavaScript
- React Hooks
- Context API
- useReducer
- Mock Data

## 3. Main Features

### Customer

- Login / Signup
- Menu browsing
- Search and categories
- Food details
- Cart management
- Promo codes
- Checkout
- Order confirmation
- Order tracking
- Table reservation
- Profile
- Dark/Light theme
- Logout

### Manager

- Order management
- Reservation management
- Menu management
- Price editing
- Availability control
- Special item management
- Logout

## 4. React Concepts Used

| Concept       | Purpose                         |
| ------------- | ------------------------------- |
| `useState`    | Manage local state              |
| `useEffect`   | Handle effects and timers       |
| `useRef`      | Manage references               |
| `useContext`  | Access shared application data  |
| `useReducer`  | Manage Cart and Order state     |
| `useMemo`     | Calculate derived data          |
| `useCallback` | Keep functions stable           |
| `React.memo`  | Reduce unnecessary re-rendering |
| Custom Hooks  | Reuse common logic              |
| `FlatList`    | Display menu lists              |

## 5. Context API

The application uses Context API to share data between multiple screens.

Main contexts:

- `AuthContext`
- `ThemeContext`
- `CartContext`
- `OrdersContext`
- `ReservationContext`
- `MenuContext`

Context helps reduce unnecessary prop drilling.

## 6. Reducers

Reducers are used for complex state management.

### Cart Reducer

Handles:

- Add item
- Remove item
- Increase quantity
- Decrease quantity
- Update note
- Apply promo
- Remove promo
- Clear cart

### Orders Reducer

Handles:

- Add order
- Update order status
- Cancel order
- Clear orders

`useReducer` is useful when multiple related state changes are required.

## 7. Custom Hooks

The project contains:

- `useForm` - manages form values and validation.
- `useDebounce` - delays search execution.
- `useReservation` - manages reservation logic.

Custom hooks make the code reusable and easier to maintain.

## 8. Mock Data

The application uses local mock data instead of a real backend.

Examples:

- Users
- Menu Items
- Categories
- Orders
- Reservations
- Tables

## 9. Demo Accounts

### Customer

Email: `customer@restaurant.com`

Password: `Customer123`

### Manager

Email: `manager@restaurant.com`

Password: `Manager123`

## 10. How to Run

Open the project folder in terminal:

```bash
cd D:\RestaurantApp
```

Install dependencies if required:

```bash
npm install
```

Start the Expo development server:

```bash
npx expo start
```

Then scan the QR code using Expo Go.

## 11. Project Structure

```text
RestaurantApp
│
├── A1
│   ├── Screenshots
│   ├── SRS
│   └── UML
│
├── assets
├── src
│   ├── app
│   ├── context
│   ├── data
│   ├── hooks
│   └── reducers
│
├── app.json
├── package.json
├── package-lock.json
├── README.md
└── tsconfig.json
```

## 12. Limitations

- No real backend
- No real database
- Mock authentication
- Orders and reservations are temporary
- No real online payment
- Mock/local application data

## 13. Future Enhancements

- Real backend
- Database integration
- Secure authentication
- Online payment
- Persistent storage
- Real-time notifications
- Customer reviews
- Real table availability

## 14. Conclusion

The Restaurant App MVP demonstrates the main restaurant workflows using React Native, Expo Router, React Hooks, Context API, reducers, custom hooks, and mock data.

The project can be extended in the future by connecting it to a real backend and database.
