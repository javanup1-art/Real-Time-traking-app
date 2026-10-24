# Logistics & Fleet Tracker - Mobile Client Application

This is the cross-platform mobile application built with **Flutter (Dart)** for the Logistics and Fleet Tracking System. It serves as the user/client-facing interface, allowing customers or dispatchers to track active deliveries, view driver locations in real-time, and manage shipment statuses directly from their mobile devices.

## 🚀 Features
* **Real-Time Map Visualization:** Live tracking of delivery vehicles with smooth, animated custom markers using WebSockets and Google Maps API / Leaflet.
* **Order Tracking & History:** Detailed overview of active, pending, and completed deliveries.
* **Instant Push Notifications:** Real-time updates regarding shipment pickup, delays, and successful deliveries.
* **Optimal Route Visualization:** Displays the recommended path from the source to the destination alongside the driver's current position.
* **Low Battery & Data Optimization:** Efficiently handles incoming background data streams to minimize device resource consumption.

## 🛠️ Tech Stack & Architecture
* **Framework:** Flutter (Dart)
* **State Management:** Provider / BLoC / GetX (Clean Architecture principles)
* **Real-Time Networking:** `socket_io_client` / WebSocket channel
* **Maps Integration:** `google_maps_flutter` or `flutter_map`
* **Local Storage:** `shared_preferences` / `hive` (for caching user session and offline orders)

## 📁 Project Structure
```text
├── lib/
│   ├── main.dart           # Application entry point
│   ├── config/             # Themes, constants, and API/WebSocket endpoints
│   ├── models/             # Data models (Driver, Order, Coordinates)
│   ├── services/           # WebSocket listener and HTTP API services
│   └── views/              # UI Screens (Login, MapView, OrderHistory)
├── pubspec.yaml            # Project dependencies and asset definitions
└── README.md               # App documentation
```

## ⚙️ Installation & Setup

1. **Prerequisites:**
   * Make sure you have the [Flutter SDK](https://flutter.dev) installed.
   * Ensure an Android Emulator, iOS Simulator, or physical device is connected.

2. **Clone the Repository:**
   ```bash
   git clone https://github.com
   cd logistics-client-flutter-app
   ```

3. **Install Dependencies:**
   Fetch all required Dart packages:
   ```bash
   flutter pub get
   ```

4. **Configure Endpoints:**
   Open `lib/config/constants.dart` (or your respective config file) and update the server URLs to point to your live Node.js backend:
   ```dart
   const String BACKEND_HTTP_URL = "http://your-server-ip:3000/api";
   const String BACKEND_WS_URL = "ws://your-server-ip:3000";
   ```

5. **Run the Application:**
   ```bash
   flutter run
   ```

## 💡 How It Connects to the Ecosystem
1. **Authentication:** The user logs in, and the app fetches active orders from the Node.js backend via REST API.
2. **Subscription:** When the user opens the tracking screen, the app sends a join request to the **WebSocket** server for that specific order ID.
3. **Live Sync:** As the driver's app emits new GPS data to the server, the server relays the coordinates to this client app instantly.
4. **UI Update:** The Flutter map updates the driver marker's latitude and longitude smoothly without needing to refresh the screen.

## 📄 License
This project is open-source and licensed under the MIT License.
