# WinterArk Testing Assignment - Manual Test Guide

This guide provides a detailed, step-by-step walkthrough for setting up, configuring, and manually testing the WinterArk app. Please follow these instructions closely to ensure a consistent testing process.

---

## Table of Contents

- [Setup and Installation](#setup-and-installation)
    - [Android Studio & Virtual Device Setup](#android-studio--virtual-device-setup)
    - [Flutter Installation & Configuration](#flutter-installation--configuration)
- [Troubleshooting: Gradle Errors](#troubleshooting-gradle-errors)
- [Manual Testing Steps](#manual-testing-steps)
    - [1. Login/Signup Page](#1-loginsignup-page)
    - [2. Workout Planner](#2-workout-planner)
    - [3. Past Workouts](#3-past-workouts)
    - [4. Gym Buddies](#4-gym-buddies)
        - [4.a Messaging Feature](#4a-messaging-feature)
        - [4.b Buddy Past Workout Viewer](#4b-buddy-past-workout-viewer)
- [Conclusion](#conclusion)

---

## Setup and Installation

### Android Studio & Virtual Device Setup

1. **Download & Update Android Studio:**
    - Download Android Studio if you haven't already.
    - Ensure it is updated to the most recent version.

2. **Create a Virtual Device:**
    - Open the Android emulator within your project.
    - On the right side of the screen, locate and click on the **Device Manager** tab.
    - Click the small plus (**+**) button at the top and select **Create Virtual Device**.
    - Under the **Phone** category, choose the **Medium Phone** option.

3. **Select the System Image:**
    - Choose the release named **VanillaIceCream** with the following specs:
        - **API Version:** 35
        - **ABI:** x86_64
        - **Target:** Android 15.0 for Google Play Store
    - If the image is not installed, click the download button and wait for the SDK Component Installer to finish. Then, click the blue **Finish** button.

4. **Finalize Virtual Device Setup:**
    - Leave all configuration settings at their defaults.
    - Your virtual device is now ready.

### Flutter Installation & Configuration

1. **Install Flutter SDK:**
    - Follow the installation instructions provided on the [Flutter Installation Guide](https://docs.flutter.dev/get-started/install).
    - You may install via VS Code or manually as per your preference.

2. **Install the Flutter Plugin in Android Studio:**
    - Go to **Settings > Plugins** in Android Studio.
    - Search for and install the **Flutter plugin**.
    - Restart Android Studio when prompted.

3. **Resolve Dependencies:**
    - Open the terminal in your project folder.
    - Run the following command:
      ```bash
      flutter pub get
      ```
    - This command will resolve any dependency issues.

4. **Launch the Emulator and Run the App:**
    - Go back to the **Device Manager** tab and click the play button to start the emulator.
    - Wait until the emulator boots to the home screen.
    - In Android Studio, select the device from the device selector dropdown (icon with a blue mobile phone outline).
    - Press the green play button to run the project.
    - When the project starts, you should see the WinterArk login/signup page on the emulator.

---

## Troubleshooting: Gradle Errors

If you encounter errors from Gradle preventing the app from running:

1. **Install JDK 17:**
    - Download and install JDK version 17 if it is not already installed.

2. **Update Project Settings:**
    - Navigate to **File > Project Structure**.
    - Change the SDK to **Oracle OpenJDK 17**.

3. **Edit the local.properties File:**
    - Locate the `local.properties` file in your project.
    - Update the following line to point to your JDK 17 installation:
      ```
      org.gradle.java.home=C:\\Program Files\\Java\\jdk-17
      ```
    - Adjust the path if your JDK 17 is installed in a different location.

After making these changes, the Gradle errors should be resolved, allowing you to run the WinterArk app successfully.

---

## Manual Testing Steps

### 1. Login/Signup Page

- **Sign Up Process:**
    1. Launch the app to view the login/signup page.
    2. Click the **Sign Up** button.
    3. Fill in the required fields:
        - **Username**
        - **Email** (ensure it is valid; a verification code will be sent)
        - **Password**
    4. Test error handling:
        - Try using an already registered email/username.
        - Input an invalid email format.
    5. Click the blue link to view the **Terms of Service** popup (currently a placeholder).
    6. Accept the Terms of Service.
    7. Submit the form.
    8. Check your email for the verification code (via the SendGrid API).
    9. Enter the verification code on the next screen.
    10. Successful verification should take you to the WinterArk landing page.

- **Sign In Process:**
    1. Use the **Sign In** option.
    2. Log in with your username or email and password.
    3. Note: The forgot password feature is still in development.

### 2. Workout Planner

- **Accessing the Workout Planner:**
    1. Tap the **Dumbbell** icon at the bottom of the screen.

- **Creating a Workout:**
    1. Select a workout split from the dropdown menu at the top.
    2. Enter the exercise details:
        - Exercise Name
        - Sets
        - Reps
        - Weight (lbs or kg)
    3. To add additional exercises, click the blue **+** button.
    4. To remove an exercise, click the red **–** button.

- **Submitting a Workout:**
    1. Pick the desired date and time.
    2. Add any additional notes if necessary.
    3. Click the blue submit button.
    4. A confirmation message should appear if the workout is submitted.
    5. Warnings will appear if required fields are missing.

### 3. Past Workouts

- **Viewing Past Workouts:**
    1. Navigate to the **Past Workouts** section.
    2. Note that currently, only workouts from the current year are displayed.
    3. Select the day when the workout was planned.
    4. The details from the Workout Planner will appear for that day.

- **Editing or Deleting Workouts:**
    1. To update a workout, click on the exercise details for that day.
    2. Make the necessary edits and press the **Update** button.
    3. Close and reopen the details to verify the update.
    4. To delete an exercise, select the workout and click the **Delete** button.
    5. A deletion confirmation notification should appear.

### 4. Gym Buddies

- **Adding a Gym Buddy:**
    1. In the Gym Buddies section, type the name or username of the target user.
    2. Press Enter to view matching profiles.
    3. Click the blue add icon to send a buddy request.
    4. The request will appear under **Outgoing Requests**.

- **Accepting a Buddy Request:**
    1. The receiving user should log into their account.
    2. Accept the incoming buddy request.
    3. The buddy will then appear in the **Connected Buddies** section.

#### 4.a Messaging Feature

- **Sending a Message:**
    1. Ensure you are already buddies with the recipient.
    2. Click the green text bubble icon next to your buddy's name.
    3. Type and send your message.
    4. The message will display with its sent time and date.
    5. When the recipient reads the message, the red notification bubble will disappear.
    6. Both users will see a receipt indicating when the message was sent and read.

#### 4.b Buddy Past Workout Viewer

- **Viewing a Buddy's Workout History:**
    1. In the Gym Buddies section, click the blue calendar icon next to a buddy's name.
    2. The buddy's workout history will be displayed.
    3. Select a day to view detailed workout entries logged by your buddy.

---

## Conclusion

By following these detailed instructions, you will have successfully set up and tested the WinterArk app. If any issues arise during the setup or testing process, refer to the troubleshooting section or contact the development team for further assistance.

*Thank you for your attention to detail. Happy testing!*
