---
name: xoid-native
description: Use when working on screens shown in xoid, the design tool showing this app live in iPhone frames. Look at and drive xoid's frames, read what the designer selected, then edit Swift with Xcode's own tools.
---

# Working with xoid's live frames

xoid shows this app running in iPhone frames on its canvas. A designer may be looking at the same frames while you work. Pass the project's absolute path as `project` on every xoid call.

## Rules

- Use xoid's frames to look at and use the app. Never use RunProject or DeviceInteraction on simulators named `xoid - …`. DeviceInteraction allows one session per simulator and moves the designer's screen under them.
- xoid builds its frames itself, in its own build folder. To see a change on a frame, use `xoid_device` with action `build_run`. Use Xcode's BuildProject only to read compile errors.
- Make the smallest Swift edit that does what was asked.
- Follow the app's String Catalog: user-facing text goes in `Localizable.xcstrings`, never as a bare literal.
- Never commit. The developer reviews and commits.
- Never edit `.xoid/ios.json` by hand. The developer changes it in xoid with Prepare for Designers.
- Change the Flow (`.xoid/flow.json`) only with `xoid_flow`: call `get` first and pass its `revision` as `expectedRevision`. If xoid refuses because the Flow changed, call `get` again and redo the change on what's there now.

## The loop

1. `xoid_selection` with action `current`: what the designer selected, with the source lines it came from.
2. Edit the Swift with XcodeUpdate.
3. `xoid_device` with action `build_run`: xoid rebuilds its frames from its own build folder. It answers within 50 s, or tells you to call `build_status`.
4. `xoid_frames` with action `screenshot`: check the change on the frame.
