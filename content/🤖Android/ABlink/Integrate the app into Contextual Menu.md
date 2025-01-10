---
title: "Introducing a Powerful New Feature in ABlink: Contextual Menu Integration"
description: Quick share with Right menu context
draft: false
tags:
  - AndroidApp
  - ABlink
  - ContextualMenu
date: 2025-01-10T16:09:58+07:00
---
Find more at:
- [android - My app with PROCESS_TEXT intent does not appear in all apps' copy-paste menu - Stack Overflow](https://stackoverflow.com/questions/72910365/my-app-with-process-text-intent-does-not-appear-in-all-apps-copy-paste-menu/72930519#72930519)
- https://dev.to/bigaru/providing-custom-text-selection-actions-in-android-1akc
---

| ![[Pasted image 20250110160556.webp\|245]] | ![[Pasted image 20250110155849.webp\|246]] | ![[Pasted image 20250110160942.webp\|246]] |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| 1. Turn on the ABlink                      | 2. Share with ABlink                       |                                            |

### Introducing a Powerful New Feature in ABlink: Contextual Menu Integration

At ABlink, we're constantly looking for ways to make sharing and interacting with your favorite content even more seamless and efficient. Today, we're thrilled to announce the latest enhancement to ABlink—integration with Android’s **contextual text selection menu**! This feature leverages the `PROCESS_TEXT` intent, providing you with a more intuitive way to interact with text directly within any app that supports it.

#### The Problem We Solved

Previously, sharing or processing text from other apps required extra steps, such as copying the text, switching to ABlink, and pasting it for further actions. While this worked, we knew it could be smoother. Inspired by the issues solved discussed in [this Stack Overflow thread](https://stackoverflow.com/questions/72910365/my-app-with-process-text-intent-does-not-appear-in-all-apps-copy-paste-menu/72930519#72930519) and guided by best practices outlined in [this developer blog post](https://dev.to/bigaru/providing-custom-text-selection-actions-in-android-1akc), we’ve implemented a feature that significantly reduces friction when processing text.

#### What’s New?

With the new contextual menu integration, ABlink now appears as an option in the text selection menu whenever you highlight text in apps that support the `PROCESS_TEXT` action. This means you can:

- **Quickly share text** to your favorite Messenger contact.
- **Analyze text** for potential scams using our VirusTotal API integration.
- **Perform other actions** directly, without leaving the current app.

#### How It Works

Here’s what happens under the hood:

1. When you select text in a compatible app, ABlink will appear in the contextual menu under the "Share" options.
2. Clicking the ABlink action sends the selected text to our app, where you already:
    - Copied the text into clipboard for future use
    - Open your contacts - ready to send

We’ve also added an intuitive action label, "(ABlink) Share," making it short and clear.

---
#### (Nerdy here) A Simple Setup for Developers

For those curious about the technical implementation, this feature uses the `PROCESS_TEXT` intent filter in the `AndroidManifest.xml` file:

```xml
<activity
    android:name=".YourActivity"
    android:permission="android.permission.PROCESS_TEXT">
    <intent-filter>
        <action android:name="android.intent.action.PROCESS_TEXT" />
        <category android:name="android.intent.category.DEFAULT" />
        <data android:mimeType="text/plain" />
    </intent-filter>
</activity>
```

To enhance user experience, we added a descriptive label with an emoji:

```xml
<string name="contextual_action_label">(ABlink) Share 📤</string>
```

This ensures ABlink stands out in the contextual menu, offering clarity and branding.

#### Why This Matters

This update saves time and makes ABlink even more accessible. Whether you’re scanning a suspicious message, sharing a quick note, or interacting with text in any supported app, ABlink now blends seamlessly into your workflow.

#### Try It Out!

To experience this new feature, update to the latest version of ABlink. Highlight any text in a compatible app, tap the contextual menu, and look for "(ABlink) Share." It’s that simple!

We’re excited to hear your feedback on this feature and how it improves your experience. Let us know your thoughts, and stay tuned for more updates as we continue to make ABlink the go-to app for sharing and security.