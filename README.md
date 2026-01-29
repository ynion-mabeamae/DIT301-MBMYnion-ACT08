# Simple Location Tracker App

A lightweight Android application that tracks and displays the user's real-time geographic location on an interactive map. This project demonstrates how to integrate OpenStreetMap (via osmdroid) and Google Play Services Location API.

## Features
*   **Real-time Tracking**: Automatically updates the user's position as they move.
*   **Live Map View**: Uses `osmdroid` to render map tiles.
*   **Location Metadata**: Displays latitude, longitude, and accuracy details in an overlay panel.
*   **Battery Efficient**: Uses the Fused Location Provider for optimized power consumption.

## Permissions Used
The app requires the following permissions to function correctly:

*   `INTERNET`: Required to download map tiles from OpenStreetMap servers.
*   `ACCESS_FINE_LOCATION`: Allows the app to access precise location from GPS and Network providers.
*   `ACCESS_COARSE_LOCATION`: Allows the app to access approximate location.
*   `ACCESS_NETWORK_STATE`: Used by the map library to check connectivity before fetching tiles.
*   `WRITE_EXTERNAL_STORAGE` (Optional/Legacy): Used for caching map tiles locally.

## How GPS Location is Obtained
The app utilizes the **Google Play Services Fused Location Provider API**. 

1.  **Permission Check**: The app first verifies if the user has granted `ACCESS_FINE_LOCATION`.
2.  **Location Request**: A request is configured with high priority (`PRIORITY_HIGH_ACCURACY`) and a specific interval (e.g., every 5-10 seconds).
3.  **Sensor Fusion**: The Fused Location Provider intelligently combines signals from GPS, Wi-Fi, and Mobile networks to provide the most accurate coordinates while minimizing battery drain.
4.  **Callback**: Whenever a new location is detected, a callback is triggered that updates the `MapView` center and refreshes the text in the location information panel.

## Screenshots
| Map View | Location Tracking |
| :---: | :---: |
| ![Main Screen](screenshots/map_location.png) | ![Tracking Active](screenshots/location_update.png) |