---
title: "ABlink: Building the Perfect 1x1 Widget (Part 2)"
draft: false
tags: 
date: 2024-12-18T16:27:55+07:00
---
![[Pasted image 20250101095418.webp]]
**TL;DR:** I designed a simple 1x1 widget with options for avatar size, cropping styles, editable title, hide title, and contact selection. Inspired by Shortcut Maker, but simpler for users.

---

**Day 2: Designing a Simple and Flexible Widget**

After diving deeper into the Android docs and learning from other developers who’ve implemented similar features, I realized ABlink only needs the simplest type of widget: a **1x1 widget**.

Why a 1x1 widget?

- It’s compact and doesn’t take up much space.
- Users can easily add **multiple shortcuts** on their home screen without clutter.

The maximum size for a 1x1 widget is clearly defined in the Android documentation, and it works perfectly for my app’s needs. I also looked at how the **Shortcut Maker app** (https://play.google.com/store/apps/details?id=rk.android.app.shortcutmaker&hl=en) approaches widget customization. Inspired by its flexibility, I decided to offer a similar feature set but keep things even **simpler** – no unnecessary steps, just a quick and easy process.

### Widget Configuration Features

Here’s what users can customize:

1. **Avatar Size**:
    
    - Three options: **Small, Medium (default), and Large**.
2. **Avatar Cropping**:
    
    - Three styles:
        - **Circle Crop**
        - **Samsung-like Round Corner**
        - **Rectangle Round Corner**
3. **Title (Contact Name)**:
    
    - Users can edit the title if they want to customize it.
    - Default: **Contact name**.
4. **Hide Title Option**:
    
    - Some users prefer a clean home screen with just the avatar.
    - This option allows hiding the title entirely.
5. **Contact Selection**:
    
    - Users can quickly pick a contact from their list to create the widget.

### Keeping It Simple

The goal is to give users enough flexibility without wasting their time. With these options, anyone can set up a clean and functional shortcut in just a few taps.

**What’s Next?**  
On Day 3, I’ll focus on implementing these features and ensuring the widget runs smoothly on different devices.

![[Pasted image 20241218110737.webp|554]]

**Tags:**  
#ABlink #Widgets #HomeScreenWidgets #UXDesign #AvatarCustomization #ShortcutCustomization #AndroidOS

---