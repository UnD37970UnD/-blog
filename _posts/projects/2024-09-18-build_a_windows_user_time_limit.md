---
layout: post
title: "Time Tracking&Limiting Program 4 Parents"
date: 2024-09-18
last_modified_at: 2024-09-18
categories: [projects]
---

## Why Create This Program?

I want to limit my brother's time on the PC because he can get a little too attached to Minecraft and forgets about his homework and other responsibilities. I know that this exist with Microsoft Parental Control but it only works with online windows users; and i have a local user.

## The ideea

- The program will be simple. During setup, it will ask for the user account to track, along with a time limit in hours and minutes (h:m). Once the user logs in, a countdown will start. When 10 minutes remain, a notification will be shown, reminding the user to save their game and any other open work, as they will soon be logged out.
- Another feature to consider is how the child could still do homework if they need the PC. I'm thinking of sending an SMS or WhatsApp message to the parent's phone with a generated code that allows temporary access for homework purposes.

## The implementation

### 1. Defining the Core Features

Before jumping into coding, I defined the core functionality of the program. The main features include:

- Selecting the user account for which screen time will be limited.
- Setting a time limit in hours and minutes.
- Starting a countdown when the user logs in.
- Sending notifications when time is running out.
- Automatically logging the user out when the time limit is reached.
- A feature to allow parents to temporarily grant more time (for homework, etc.).

### 2. Choosing the Tech Stack

For this project, I had to decide which programming language and tools would work best for the task. Given the need for Windows-specific features like managing user logins and sending notifications, I decided on:

- **Python**: For its ease of use and extensive libraries for both GUI and system-level control.
- **Tkinter**: For building a simple, user-friendly GUI.
- **pywin32**: To interact with Windows user accounts and manage logins.
- **time or schedule libraries**: To handle the countdown timer and triggers.

### 3. Program Structure

The program is divided into three key components:

#### 3.1. User Setup

The setup allows the parent (or admin) to:

- Select the user account whose screen time will be limited.
- Input the time limit in hours and minutes (e.g., 1 hour, 30 minutes).

For this, the GUI (built with Tkinter) will have:

- A dropdown menu to select the user.
- Time limit input fields.
- A save button to store the configuration.

#### 3.2. Countdown Timer and User Notification

Once the user logs in, the countdown will start in the background. As the time decreases:

- When 10 minutes are left, the program will trigger a desktop notification using a library like `plyer`.
- The user will be informed to save their progress before they are logged out.

This part involves checking the user's login time and triggering notifications or actions at set intervals.

#### 3.3. Auto-Logout Feature

When the time limit is reached:

- The program will automatically log the user out by invoking Windows API commands (using `pywin32` or `os` commands).
- This ensures that the user can't continue using the PC until the parent grants more time or the next allowed session starts.

#### 3.4. Temporary Access for Homework

If the child needs to use the PC for homework:

- The program can send a notification to the parent (via SMS or WhatsApp) with a code that temporarily unlocks the PC for homework purposes.
- Using services like **Twilio** for SMS or **WhatsApp Business API** could make this part of the system work.

### 4. Implementing the Code

In this section, I wrote the code in small, manageable pieces:

#### 4.1. The GUI Setup

A simple Tkinter GUI to input the user and time limit.
