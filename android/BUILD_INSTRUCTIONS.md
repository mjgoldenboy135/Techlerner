# TechLearner – Bow Fun  
## Android App Build Guide

---

### What's included
| Path | Description |
|---|---|
| `app/src/main/assets/game/index.html` | Full HTML5 game (35 KB, no internet needed) |
| `app/src/main/java/…/MainActivity.java` | Full-screen WebView host activity |
| `keystores/techlearner-release.jks` | **Release signing keystore** (keep this file safe!) |
| `app/build.gradle` | Already wired to the keystore for release builds |

---

### Step 1 – Prerequisites
- **Android Studio** Hedgehog 2023.1 or newer  
  Download: https://developer.android.com/studio  
- Android SDK Platform **34** + Build Tools **34.0.0** (Android Studio installs these automatically)

---

### Step 2 – Open the project
1. Launch Android Studio  
2. **File → Open** → select the `android/` folder (this folder)  
3. Wait for Gradle sync to finish (~1–2 minutes on first run)

---

### Step 3 – Build the signed AAB

#### Option A – Android Studio GUI (easiest)
1. Menu: **Build → Generate Signed Bundle / APK**  
2. Choose **Android App Bundle**  
3. Click **Choose existing** keystore:  
   - File: `keystores/techlearner-release.jks`  
   - Store password: `TechLearner@2024`  
   - Key alias: `techlearner`  
   - Key password: `TechLearner@2024`  
4. Select **release** build variant → **Finish**  
5. AAB saved to: `app/release/app-release.aab`

#### Option B – Command line
```bash
# macOS / Linux
./gradlew bundleRelease

# Windows
gradlew.bat bundleRelease
```
Output: `app/build/outputs/bundle/release/app-release.aab`

---

### Step 4 – Verify the AAB is signed
```bash
# Install bundletool (https://github.com/google/bundletool/releases)
java -jar bundletool.jar validate --bundle=app-release.aab
```

---

### Step 5 – Upload to Google Play

1. Go to https://play.google.com/console  
2. **Create app** → App name: `TechLearner - Bow Fun`  
3. **Package name**: `com.techlearner.bowfun`  
4. **Production → Releases → Create new release**  
5. Upload `app-release.aab`  
6. Fill in **store listing** details below  

---

### Google Play Store Listing (ready to copy-paste)

**App name:** TechLearner – Bow Fun  
**Short description (80 chars):**  
> Aim, pull & shoot! A colourful bow-and-arrow game for toddlers.

**Full description (4000 chars max):**
> 🏹 TechLearner – Bow Fun is the perfect first game for children ages 3–6!
>
> Kids aim a bow at adorable cartoon animals — a fluffy bunny, a quacking duck, a silly cat, a clucking chicken, and a cuddly bear — that walk, hop, and fly across the screen. Pull back the bowstring and release to shoot! Every hit bursts into a rainbow of stars, sounds, and colourful particles.
>
> ✨ FEATURES
> • 5 cute cartoon animals with unique movement (walking, hopping, flying)
> • Neon glow effects and sparkle trails — kids love the visuals!
> • Satisfying sound effects on every hit
> • Combo streak system — encourages repeated play
> • Rainbow animated sky, wobbling flowers, glowing sun
> • NO ads · NO in-app purchases · NO internet required
> • Works completely offline
> • Large touch targets — perfect for little fingers
> • Landscape full-screen: fills the whole tablet or phone
>
> 🎨 Designed for toddlers and early learners. Simple one-finger gameplay: hold to aim, release to shoot.

**Category:** Games → Action  
**Content rating:** Everyone (ESRB E / PEGI 3)  
**Target age group:** Ages 3–6  
**Contains ads:** No  
**In-app purchases:** No  

---

### Keystore – IMPORTANT
| Field | Value |
|---|---|
| File | `keystores/techlearner-release.jks` |
| Store password | `TechLearner@2024` |
| Key alias | `techlearner` |
| Key password | `TechLearner@2024` |

> ⚠️ **Back up `techlearner-release.jks` to a safe location.**  
> You must use the same keystore for every future update.  
> If you lose it you cannot update your app on Google Play.

---

### App details summary
| Field | Value |
|---|---|
| Package name | `com.techlearner.bowfun` |
| Version code | 1 |
| Version name | 1.0 |
| Min SDK | Android 5.0 (API 21) |
| Target SDK | Android 14 (API 34) |
| Orientation | Landscape |
| Internet required | No (game runs fully offline) |
