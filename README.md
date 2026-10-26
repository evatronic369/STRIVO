# STRIVO — Modern Interactive Guitar Learning App

A full-featured, modern guitar learning application for Android built with **Jetpack Compose**, **Kotlin**, and real-time audio processing. 

STRIVO turns practice into an engaging experience: play along with an interactive 6-string note highway, get evaluated through the device microphone or virtual strings, tune with a chromatic tuner, study 26+ chord shapes, and master 15 progressive worlds spanning 106 structured lessons.

---

## 🚀 Key Features

- **🎮 Interactive 6-String Note Highway (Yousician Style)**:
  - 6 horizontal animated guitar strings with realistic vibration physics.
  - Floating fret blocks and chord target labels with finger placement guides.
  - **Wait-On-Miss Practice Mode**: Automatically pauses the highway when you miss a note or chord, resuming seamlessly once you hit the correct pitch.
  - Dual Input: Real microphone pitch detection (YIN/autocorrelation) and instant touch-to-play fallback.
  - Live scoring, hit accuracy percentage, combo streak counters, and star ratings.

- **🗺️ Progressive Sequential Curriculum**:
  - **15 Structured Worlds & 106 Lessons**: From posture and open string basics to barre chords, pentatonic improvisation, and fingerstyle classics.
  - **Sequential Unlock System**: Level 1 is unlocked initially; each subsequent lesson unlocks after passing the prior exercise.
  - **Automatic Section Advancement**: Completing the final lesson of a section automatically celebrates mastery, unlocks the next world, and transitions the learner to the new section.

- **🎸 Real-Time Audio & Practice Suite**:
  - **Pro Chromatic Tuner**: Real-time microphone listening, needle cents deviation (-50 to +50 cents), Hz frequency readout, and reference string tone playback.
  - **24-Fret Fretboard & Chord Library**: Interactive audio chord playback, finger placement numbers, and musical scale overlays.
  - **Audio Metronome**: 40–260 BPM, tap tempo, time signatures (4/4, 3/4, 6/8), and crisp percussion audio clicks.
  - **Song Practice Studio**: Built-in practice tracks and custom song importer with interactive audio playback, waveform scrubbing, A-B looping, and speed adjustment.

- **🏆 Gamification & Offline Persistence**:
  - XP rewards, player levels, daily missions, and practice streak tracking.
  - 100% offline persistence using local Room SQLite database (no accounts or logins required).

---

## 🛠️ Tech Stack & Architecture

- **UI Framework**: Android Jetpack Compose with Material Design 3 (M3)
- **Language**: Kotlin 2.0+
- **Architecture**: Clean MVVM (Model-View-ViewModel) with Kotlin Coroutines & `StateFlow`
- **Audio Analysis**: Android `AudioRecord` streaming 16-bit PCM (44.1 kHz) into autocorrelation & YIN pitch tracking
- **Audio Synthesis**: Low-latency `AudioTrack` physical string modeling and metronome tick generator
- **Local Database**: Android Jetpack Room with SQLite
- **Build System**: Gradle Kotlin DSL (`build.gradle.kts`) with Version Catalog (`libs.versions.toml`)

---

## 📦 Getting Started & Building

### Prerequisites
- Android Studio Hedgehog (2023.1.1) or newer
- JDK 17 or higher
- Android SDK with `minSdk = 26`, `compileSdk = 35`, and `targetSdk = 35`

### Clone and Run
1. Clone this repository to your local machine:
   ```bash
   git clone https://github.com/<your-username>/strivo-guitar-app.git
   cd strivo-guitar-app
   ```
2. Open the project folder in **Android Studio**.
3. Let Gradle sync dependencies automatically.
4. Select an Android emulator (or connect a physical Android device via USB debugging).
5. Click **Run** (`Shift + F10`) or press the green Play button.

### Command Line Build
To compile and assemble the debug APK from the terminal:
```bash
# On Linux / macOS:
./gradlew assembleDebug

# On Windows:
gradlew.bat assembleDebug
```
The output APK will be generated at:
`app/build/outputs/apk/debug/app-debug.apk`

---

## 📁 Project Structure

```
├── app/
│   ├── src/main/java/com/example/
│   │   ├── audio/          # PitchDetector, AudioSynthesizer (Karplus-Strong)
│   │   ├── data/           # Room Database, DAO, Entities, StrivoRepository
│   │   ├── model/          # CurriculumData (15 worlds, 106 lessons), Chords, Models
│   │   ├── ui/
│   │   │   ├── components/ # Reusable Compose components, rating stars, cards
│   │   │   ├── screens/    # HomeScreen, LearnScreen, NoteHighwayScreen, Practice, Songs
│   │   │   └── theme/      # M3 Colors, Typography, Shapes
│   │   └── viewmodel/      # MainViewModel managing state flows
│   ├── src/main/res/       # Vector drawables, custom app icons, strings
│   └── build.gradle.kts    # App-level dependencies
├── gradle/
│   ├── wrapper/            # Gradle wrapper files
│   └── libs.versions.toml  # Centralized dependencies version catalog
├── build.gradle.kts        # Root build configuration
├── settings.gradle.kts     # Project name & module setup
└── README.md
```

---

## 📄 License
This project is open-source and free to use for personal practice, education, and guitar learning.
