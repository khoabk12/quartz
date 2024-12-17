---
title: "ABlink: Fixing Contact Shortcuts on Android (Part 1)"
draft: false
tags: 
date: 2024-12-12T13:52:45+07:00
---
![[Pasted image 20241217222441.png]]

**TL;DR:** Pinned shortcuts add app icons by default. I found that widgets can display a cleaner layout, so I’m switching to widgets for custom shortcuts.

---

**Day 1: The Shortcut Problem**  
I added a "pinned shortcut" feature to ABlink so users could create quick access to a contact on their home screen. It worked, but there was one problem:

The shortcut showed the contact's **avatar** but also added **ABlink’s app icon** at the bottom-right. It didn’t look clean – I wanted the shortcut to show **only the avatar and the contact’s name**.

### The Fix

I did some research and found that **Android widgets** are the solution. Widgets let developers design custom layouts for the home screen and handle clicks. Unlike pinned shortcuts, widgets can display content exactly how you want it – no extra icons.

### What’s Next?

Next, I’ll design a widget that only shows the avatar and contact name, just as I imagined.

**Tags:**  
#ABlink #AndroidDevelopment #Widgets #HomeScreenCustomization #PinnedShortcuts #CleanDesign

_(Check out Android’s developer docs [here](https://developer.android.com/develop/ui/views/appwidgets))_
https://www.geeksforgeeks.org/how-to-create-a-basic-widget-of-an-android-app/