﻿# Training Log App 🏋️

A modern Android fitness tracking application built with Jetpack Compose that helps users log workouts, track progress, set goals, and analyze their training performance over time.

## 📋 Project Overview

**Problem**: Gym-goers need an efficient way to track their workouts, monitor progress, and ensure progressive overload without carrying notebooks or juggling complex spreadsheets.

**Solution**: Training Log App provides a streamlined mobile experience for logging exercises, automatically calculating personal records, visualizing progress with interactive charts, and organizing workouts with templates and goals.

**Key Highlights**:
- 📊 **Automatic PR Tracking**: Calculates 1RM, max weight, max reps, and volume automatically
- 📈 **Progress Visualization**: Interactive charts showing strength trends over time
- 🎯 **Smart Goal Setting**: Track progress toward specific exercise goals
- 📝 **Template System**: Save and reuse workout routines
- 🌓 **Dark/Light Theme**: Comfortable viewing in any lighting condition
- 💾 **Local-First**: All data stored securely on device using Room database

## 📱 Features
### Core Functionality
- **Workout Logging**: Create and save detailed workout sessions with multiple exercises
- **Exercise Tracking**: Log sets, reps, and weights for each exercise
- **Workout History**: View all past workouts with detailed exercise breakdowns
- **Exercise Search**: Quickly find and view specific exercises from your history
### Progress & Analytics
- **Personal Records**: Automatic tracking of your best performances (1RM, max weight, max reps, max volume)
- **Exercise Progress Charts**: Visual progress tracking with multiple chart types:
  - Strength progression (estimated 1RM)
  - Max weight over time
  - Total volume trends
  - Average weight progression
- **Progress Insights**: Percentage improvements and performance metrics
### Goals & Templates
- **Goal Setting**: Create and track exercise-specific goals with progress monitoring
- **Workout Templates**: Save frequently used workout routines for quick access
- **Template-Based Workouts**: Start new workouts from saved templates
- **Goal Progress Tracking**: Visual progress bars and completion status
### User Experience
- **Dark/Light Theme**: Toggle between themes with persistent preferences
- **Bottom Navigation**: Easy access to all main sections
- **Exercise Autocomplete**: Smart suggestions based on previously used exercises
- **Snackbar Notifications**: User-friendly feedback for actions
- **Material Design 3**: Modern, clean UI with premium color scheme
## 🛠️ Technical Stack
### Architecture & Libraries
- **Language**: Kotlin
- **UI Framework**: Jetpack Compose
- **Architecture**: MVVM (Model-View-ViewModel)
- **Database**: Room (SQLite)
- **Navigation**: Jetpack Navigation Compose
- **Charts**: YCharts library
- **Minimum SDK**: Android 10 (API 29)
- **Target SDK**: Android 15 (API 35)

### Architecture Explanation
The app follows **MVVM (Model-View-ViewModel)** architecture pattern:

- **Model (Data Layer)**: 
  - Room database entities (`Workout`, `Exercise`, `ExerciseSet`, `Goal`, `WorkoutTemplate`)
  - Repository pattern (`WorkoutRepository`, `GoalRepository`) for data access abstraction
  - DAO (Data Access Objects) for database operations

- **ViewModel**: 
  - `MainViewModel` manages UI state and business logic
  - Handles theme preferences, workout data, and template selection
  - Exposes reactive state using Compose's `State` objects

- **View (UI Layer)**: 
  - Pure Compose UI components
  - Screens observe ViewModel state and react to changes
  - Clean separation between UI and business logic

**Benefits**: Testable code, clear separation of concerns, reactive UI updates, lifecycle-aware components

### Key Dependencies
```gradle
- Jetpack Compose BOM
- Room 2.8.4 (Database)
- Navigation Compose 2.7.6
- Material Icons Extended
- YCharts 2.1.0 (Progress visualization)
```
## 🏗️ Project Structure
```
app/src/main/java/com/example/traininglogapp/
├── MainActivity.kt                    # Main entry point
├── MainViewModel.kt                   # Central ViewModel
├── ThemePreferences.kt               # Theme persistence
├── database/
│   ├── AppDatabase.kt                # Room database
│   ├── WorkoutDao.kt                 # Workout data access
│   ├── GoalDao.kt                    # Goal data access
│   ├── WorkoutRepository.kt          # Workout data layer
│   ├── GoalRepository.kt             # Goal data layer
│   ├── Workout.kt                    # Workout entity
│   ├── Exercise.kt                   # Exercise entity
│   ├── ExerciseSet.kt                # Set entity
│   ├── Goal.kt                       # Goal entity
│   └── WorkoutTemplate.kt            # Template entity
├── ui/theme/
│   ├── Theme.kt                      # App theming
│   ├── Color.kt                      # Color definitions
│   ├── NewWorkoutScreen.kt           # Workout creation UI
│   ├── WorkoutList.kt                # History display
│   ├── AnalyticsPage.kt              # Analytics & records
│   ├── GoalsAndTemplatesPage.kt      # Goals & templates UI
│   ├── ExerciseSearchScreen.kt       # Exercise search
│   ├── ExerciseDetailScreen.kt       # Exercise details
│   ├── ExerciseProgressChart.kt      # Progress charts
│   ├── PersonalRecords.kt            # PR calculations
│   ├── GoalManager.kt                # Goal management
│   └── TemplateManager.kt            # Template management
└── res/
    └── values/
        └── strings.xml               # Localized strings
```
## 🎨 Design
### Color Scheme
- **Light Theme**: Clean white cards on light gray background
- **Dark Theme**: Dark surfaces with high contrast
- **Accent Colors**: Muted purple (#6C63FF) and soft green (#4CAF50)
- **Text**: Professional dark gray (#2B2B2B) in light mode
### Navigation
- **Bottom Navigation Bar**: Quick access to 4 main sections
  - History: View past workouts
  - New Workout: Log new training session
  - Analytics: View records and statistics
  - Goals: Manage goals and templates
- **Floating Action Button**: Quick exercise search from history

## 💡 How It Works

### User Flow
1. **Create Workouts**: Users start a new workout session and add exercises with sets, reps, and weights
2. **Track Progress**: Every workout is automatically saved and analyzed for personal records
3. **View Analytics**: Visualize strength progression with interactive charts showing 1RM estimates, max weights, and volume over time
4. **Set Goals**: Create specific exercise goals (e.g., "Bench Press 100kg") and track progress with visual indicators
5. **Use Templates**: Save frequently used workout routines as templates for quick workout creation
6. **Search History**: Quickly find any exercise from workout history using the search feature

### Key Workflows
- **New Workout Flow**: Select exercises → Log sets/reps/weights → Save workout → Automatic PR detection
- **Progress Tracking**: View exercise → See progress charts → Analyze trends → Set new goals
- **Template Usage**: Create template from workout → Save for reuse → Start workout from template

### Data Persistence
All data is stored locally using Room database with proper relationships and cascade deletion. The app uses MVVM architecture to maintain clean separation between UI and business logic.


## 📊 Database Schema
### Tables
- **workouts**: Stores workout sessions (date, name, notes)
- **exercises**: Stores exercises within workouts
- **exercise_sets**: Stores individual sets (reps, weight)
- **goals**: Stores user fitness goals
- **workout_templates**: Stores reusable workout templates
### Relationships
- One-to-Many: Workout → Exercises
- One-to-Many: Exercise → Sets
- Cascade deletion for data integrity
## 🔧 Configuration
### Theme Preferences
Theme selection is persisted using SharedPreferences and automatically restored on app launch.
### Database Migrations
Current version: 2
Note: Using destructive migration for development. Proper migrations should be added for production.

## 🐛 Known Issues
- None currently reported
## 🤝 Contributing
This is a personal project.

## 👤 Author
**Eeri Hyppänen**
- GitHub: [@eerihyppanen](https://github.com/eerihyppanen)

## 📱 Screenshots

### Main Features
<table>
  <tr>
    <td align="center"><b>New Workout</b><br/>Log exercises with sets, reps, and weights<br/><br/><img src="https://github.com/user-attachments/assets/e116bd33-57dc-47d4-8c77-dae7d5726bdf" width="200" alt="New Workout Screen"/></td>
    <td align="center"><b>Workout History</b><br/>View all past workouts chronologically<br/><br/><img src="https://github.com/user-attachments/assets/faf7262f-54da-44d0-afae-5bb8b3c93fde" width="200" alt="Workout History"/></td>
    <td align="center"><b>Analytics</b><br/>Track personal records and statistics<br/><br/><img src="https://github.com/user-attachments/assets/a80020fb-1983-469b-b202-c03911955809" width="200" alt="Analytics Page"/></td>
  </tr>
</table>

### Progress & Goals
<table>
  <tr>
    <td align="center"><b>Progress Charts</b><br/>Visualize strength progression over time<br/><br/><img src="https://github.com/user-attachments/assets/df8ab4f9-87c2-41b9-bcd4-d217a996bfbc" width="200" alt="Progress Charts"/></td>
    <td align="center"><b>Goals</b><br/>Set goals<br/><br/><img src="https://github.com/user-attachments/assets/bdcc51d1-7a2c-4963-8f77-12f48c116faf" width="200" alt="Goals"/></td>
    <td align="center"><b>Templates</b><br/>Save workout routines<br/><br/><img src="https://github.com/user-attachments/assets/d041ee4a-4a5a-4c40-9000-50da9820b792" width="200" alt="Templates"/></td>
  </tr>
</table>

### Themes
<table>
  <tr>
    <td align="center"><b>Light Theme</b><br/>Clean, professional design<br/><br/><img src="https://github.com/user-attachments/assets/e116bd33-57dc-47d4-8c77-dae7d5726bdf" width="200" alt="Light Theme"/></td>
    <td align="center"><b>Dark Theme</b><br/>Easy on the eyes for night workouts<br/><br/><img src="https://github.com/user-attachments/assets/093147c6-9691-4ede-9b24-fea662443387" width="200" alt="Dark Theme"/></td>
  </tr>
</table>



---

**Version**: 1.0
**Status**: Active Development
