---
title: How to Fix Gradle and Java Compatibility Issues in Android Studio Ladybug
draft: false
tags:
  - Gradle
  - Java Compatibility
  - Kotlin
  - Android Studio
  - KMM
date: 2025-01-10T16:10:41+07:00
---


## **TL;DR**
If you’re encountering Gradle or Java compatibility issues in Android Studio Ladybug, ensure Gradle 7.4.2 is paired with Java 11/17, or upgrade Gradle/AGP for Java 21. 🎯

## **Quick Fix**

### Gradle & AGP Errors ⚙️
1. **Upgrade Gradle to 7.4.2:** Update `gradle-wrapper.properties`:
   ```properties
   distributionUrl=https\://services.gradle.org/distributions/gradle-7.4.2-bin.zip
   ```
   Apply the update:
   ```bash
   ./gradlew wrapper --gradle-version 7.4.2
   ```

2. **Update AGP to 7.3.1:** Modify `build.gradle.kts`:
   ```kotlin
   classpath("com.android.tools.build:gradle:7.3.1")
   ```

3. **Ensure Compatible Firebase Plugins:**
   ```kotlin
   classpath("com.google.firebase:firebase-crashlytics-gradle:2.9.4")
   classpath("com.google.firebase:perf-plugin:1.4.2")
   classpath("com.google.firebase:firebase-appdistribution-gradle:3.1.1")
   ```

### Java Incompatibility 🖥️
1. **Switch to Java 11 or 17:**
   ```bash
   sudo apt install openjdk-11-jdk
   sudo update-alternatives --config java
   ```

2. **Set Gradle JDK in Android Studio:**
   Navigate to:
   ```
   File > Settings > Build, Execution, Deployment > Build Tools > Gradle > Gradle JDK
   ```
   Select **JDK 11** or **JDK 17**.

### Optional for Java 21 🚀
1. **Upgrade Gradle to 8.3:**
   ```properties
   distributionUrl=https\://services.gradle.org/distributions/gradle-8.3-bin.zip
   ```

2. **Upgrade AGP to 8.1.1:**
   ```kotlin
   classpath("com.android.tools.build:gradle:8.1.1")
   ```

3. **Use Kotlin 1.9.0:**
   ```kotlin
   classpath("org.jetbrains.kotlin:kotlin-gradle-plugin:1.9.0")
   ```

---

## **Introduction**

Three years after starting my **NewSound project**, I decided to revisit it. This was my first experiment with **Kotlin Multiplatform Mobile (KMM)**, inspired by its promise to share code across Android and iOS. 🚀

At the time, I wasn’t impressed by React Native or Flutter. KMM felt like the future, so I dived in to build an app. Revisiting the project now in **Android Studio Ladybug (2021.2.1)** brought unexpected compatibility issues.

---

## **How I Fixed This**

### Attempt 1: Ignoring Updates ❌
I opened the project in Ladybug, hoping it would build. Instead, I got:

```
Caused by: org.gradle.api.GradleException: Cannot use @TaskAction annotation on method IncrementalTask.taskAction$gradle_core()
```

### Attempt 2: Upgrading Gradle ⚙️
- Updated `gradle-wrapper.properties`:
  ```properties
  distributionUrl=https\://services.gradle.org/distributions/gradle-7.4.2-bin.zip
  ```
- Ran:
  ```bash
  ./gradlew wrapper --gradle-version 7.4.2
  ```

#### Outcome:
Gradle errors cleared, but Java compatibility became an issue.

### Attempt 3: Downgrading Java 🖥️
- Installed Java 11:
  ```bash
  sudo apt install openjdk-11-jdk
  ```
- Configured Android Studio to use **JDK 11** for Gradle tasks.

#### Outcome:
This resolved the build issues completely!

---

## **Experiences**

### Lessons Learned ✨
1. **Version Alignment is Key:** Gradle, AGP, and Java versions must match.
2. **Stay Updated:** Regular updates prevent breaking changes from piling up.
3. **Document Everything:** Notes on dependencies and versions save time later.
4. **KMM Has Evolved:** It’s exciting to see how far KMM has come since its early days.

---

### **Tags**
- #Gradle
- #JavaCompatibility
- #KotlinMultiplatform
- #KMM
- #AndroidStudio
- #Development
- #Firebase

---

With these fixes, my **NewSound** project runs perfectly in Android Studio Ladybug. If you face similar issues, I hope this guide helps! Let me know your thoughts or questions. ✨

