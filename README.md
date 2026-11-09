# Respring One Tap

A lightweight, single-page web tool designed to trigger a potential SpringBoard restart (respring) on iOS by stressing Safari's WebKit rendering engine.

No installation, jailbreak, or external dependencies required.

## Features

- **One-Tap Execution** — Start the process with a single button.
- **Auto-Run Support** — Automatically execute when the URL ends with `#go`.
- **Cooldown Protection** — Prevent repeated automatic execution within 60 seconds.
- **Standalone HTML** — Everything is contained in one HTML file.
- **Mobile-Friendly** — Minimal dark interface optimized for mobile browsers.
- **No External Dependencies** — Built using vanilla HTML, CSS, and JavaScript.

## How to Use

### Manual Mode

1. Open the hosted webpage in Safari on your iOS device.
2. Tap **Restart SpringBoard**.
3. The script will begin stressing the WebKit rendering engine.

### Auto-Run Mode

Append `#go` to the webpage URL:

`https://your-domain.com/#go`

The script will automatically execute when the page loads, provided the cooldown period has expired.

The `#go` fragment is removed from the URL before execution to help prevent accidental re-execution when Safari restores the page.

## How It Works

The script attempts to overload WebKit through two techniques:

**1. GPU / Rendering Stress**

Creates 700 full-screen elements with intensive CSS backdrop blur effects, high opacity, individual transforms, and increasing z-index values.

**2. History API Stress**

Continuously calls `history.pushState()` using a 1 ms interval to generate additional browser processing overhead.

These operations are intended to put significant pressure on the browser's rendering and processing resources.

Depending on the device and iOS version, this may cause Safari to freeze, reload, terminate, or potentially trigger a SpringBoard restart.

## Cooldown System

Automatic execution includes a 60-second cooldown using `localStorage`.

- Auto-run is triggered only by `#go`.
- The trigger is removed before execution.
- Repeated automatic execution is blocked during the cooldown.
- Manual execution remains available.
- Each page instance can start the process only once.

## Compatibility

Designed primarily for Safari on iOS and iPadOS.

Actual behavior depends on the device, operating system version, WebKit implementation, and available system resources.

**A successful respring is not guaranteed.** The script does not directly invoke any native iOS restart functionality.

## Disclaimer

This project is provided for educational and experimental purposes only.

Running the script may cause browser instability, temporary freezing, page crashes, or unexpected application termination.

Save any important work before using it.

Use at your own risk.
