# **Flight Search App**

A simple Android app built with Jetpack Compose that lets users search for airports by IATA code or name, view details, and manage favorite routes. The app uses a pre-populated Room database for offline data and Jetpack DataStore for persisting user preferences.

## **Features**

- Search Airports
  - Search by IATA code or partial/full airport name
  - Live filtering as you type
- Flight Details Screen
  - Displays departure and destination airports
- Favorites
  - Mark/unmark routes as favorites
  - Persist favorites in Room database
  - View a list of saved favorite routes on the home screen
- Offline Data
  - Pre-populated Room database (flight_search.db in assets/database/)
- User Preferences
  - Stores last-search query using Jetpack DataStore

## **Architecture**

```
com.example.flightsearchapp
├── MainActivity.kt           // Entrypoint, sets up Compose theme and FlightSearchApp()
├── FlightApplication.kt      // Initializes AppContainer & DataStore 
├── FlightSearchApp.kt        // Sets up NavigationHost & composable routes
│
├── di/                       // Dependency injection
│   ├── AppContainer.kt       // DI interface
│   └── AppDataContainer.kt   // Provides OfflineFlightRepository
│
├── data/
│   ├── FlightDatabase.kt     // Room database definition
│   ├── FlightDao.kt          // DAO for Airport & Favorite entities
│   ├── OfflineFlightRepository.kt // Repository implementation
│   ├── FlightRepository.kt   // Repository interface
│   ├── UserPreferencesRepository.kt // Jetpack DataStore helper
│   └── MockData.kt           // Sample airport data (used for testing)
│
├── model/
│   ├── Airport.kt            // Room entity for airports
│   └── Favorite.kt           // Room entity for favorites
│
└── ui/
    └── screens/
        ├── search/
        │   ├── SearchScreen.kt
        │   ├── SearchTextField.kt
        │   ├── SearchResults.kt
        │   ├── AirportRow.kt
        │   ├── FavoriteResult.kt
        │   ├── SearchViewModel.kt
        │   └── SearchUiState.kt
        └── flight_screen/
            ├── FlightScreen.kt
            ├── FlightRow.kt
            └── FlightScreenDestination.kt
```

## **Getting Started**

### Prerequisites
- Android Studio Bumblebee or later
- Android SDK 31 or higher
- Kotlin 1.7.0+
- Gradle 7.2+

### Installation
```
Clone the repository
git clone https://github.com/yourusername/flight-search-compose.git
cd flight-search-compose
```

- Open in Android Studio
  - Select File ▶ Open and choose the project folder.
- Build & Run
  - Allow Gradle to sync.
  - Run on an emulator or connected device.

### Usage

- Home Screen
  - Displays your saved favorite routes (if any).
  - Shows “No Favorites yet” when empty.

- Search Airports
  - Tap the search field and type an IATA code (e.g., “JFK”) or part of an airport name.
  - Select an airport from the filtered list to view flight details.

- Flight Details
  - Displays departure and destination airports.
  - Tap the heart icon to add/remove from favorites.

- View Favorites
  - Return to home (clear search field) to see updated favorites list.

- Dependencies
  - Jetpack Compose (UI)
  - Navigation Compose
  - Room (Local database)
  - DataStore (Preferences)
  - Coroutines + Flow (Asynchronous data streams)
  - Hilt (Optional – currently manual DI via AppContainer)

## **Credits**

This project is based on the Basic Android Kotlin Compose Flight Search codelab on developer.android.com.
https://developer.android.com/codelabs/basic-android-kotlin-compose-flight-search?continue=https%3A%2F%2Fdeveloper.android.com%2Fcourses%2Fpathways%2Fandroid-basics-compose-unit-6-pathway-3%23codelab-https%3A%2F%2Fdeveloper.android.com%2Fcodelabs%2Fbasic-android-kotlin-compose-flight-search#4
