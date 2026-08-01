# Wearable Sensor Data

Android app made of two modules (**wear** + **mobile**) that reads sensor data from a Wear OS smartwatch and streams it in real time to the paired smartphone, using Google's Wearable Data Layer API.

<p align="center">
  <img src="presentation-mockup/image1.png" width="200" />
  <img src="presentation-mockup/image2.png" width="200" />
</p>

## How it works

- On the **watch**, a foreground service registers as a listener on the available sensors and sends a message to the phone whenever a value changes (with a minimum interval of 0.1s between sends).
- On the **phone**, the app receives the messages via `MessageClient` and updates the dashboard in real time with the incoming values.
- The connection between the two devices is handled through `CapabilityClient`/`NodeClient`: the app automatically detects whether the watch is paired and whether it has the app installed, showing a button to install it from the Play Store if it doesn't.

## Supported sensors

- Accelerometer
- Gyroscope
- Magnetometer
- Heart rate
- Light
- Ambient temperature
- Relative humidity
- Proximity
- Atmospheric pressure

## Requirements

- Android Studio (Giraffe or later recommended)
- JDK 17
- A paired Android phone and Wear OS smartwatch (physical devices are needed for full functionality, especially for sensors like heart rate, which emulators don't support)

## Getting started

1. Clone the repo:
   ```bash
   git clone https://github.com/m-lomba/wearable-sensor-data.git
   ```
2. Open the project in Android Studio.
3. Build and install the `mobile` module on the phone and the `wear` module on the smartwatch.
4. Open both apps: once the pairing is detected, sensor data will start appearing on the phone's dashboard.

## Tech stack

- Kotlin + Coroutines
- Android Jetpack (ViewBinding, Lifecycle)
- Wearable Data Layer API (`CapabilityClient`, `MessageClient`, `NodeClient`, `RemoteActivityHelper`)

## License

Source files include Apache 2.0 license headers. If you'd like the license to be explicit for anyone visiting the repo, consider adding a `LICENSE` file at the project root.
