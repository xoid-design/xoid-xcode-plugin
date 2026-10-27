# xoid for Xcode

Gives Xcode 27's agents xoid's tools: they look at and use the live iPhone frames on xoid's canvas, read what the designer selected, and edit Swift with Xcode's own tools.

## Install

In xoid (Developer Tools on), choose **Help › Set Up Xcode Agent…** and follow the steps. It checks this Mac, then adds the plug-in to Xcode.

You can also add it by hand: in Xcode, open **Settings › Intelligence › Plug-ins**, choose **Add from file**, and pick this folder.

## What it needs

- macOS 26.6 or later, and Xcode 27 or later.
- xoid, opened at least once. The plug-in starts xoid's helper (`xoid.app/Contents/Helpers/xoid-mcp`), which connects to xoid on this Mac only.
- In xoid, the Xcode connection turned on. The first time Xcode's assistant uses xoid, xoid asks.

## Privacy

Your Swift code goes to the company behind the agent you pick in Xcode (Anthropic, OpenAI or Google), under your agreement with them. It doesn't go through xoid.
