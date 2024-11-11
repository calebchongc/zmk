---
title: Pointers
---

ZMK supports physical pointing devices, as well as [mouse emulation behaviors](../keymaps/behaviors/mouse-emulation.md) for sending HID pointing events to hosts.

## Configuration

To enable the pointer functionality, you must set `CONFIG_ZMK_MOUSE=y` in your config. See the [pointer configuration](../config/pointers.md) for the full details.

:::warning

When enabling the feature, changes are made to the HID report descriptor, which may not get picked up automatically over BLE to some hosts. Be sure to remove and re-pair to your hosts once you enable the feature

:::

## Mouse Emulation

Mouse emulation allows you to use your keyboard as a pointing device without using dedicated pointer hardware, like an integrated trackpad, trackball, etc. By adding new bindings in your keymap like `&mmv MOVE_UP` you can make key presses send mouse HID events to your connected hosts.

See the [mouse emulation behaviors](../keymaps/behaviors/mouse-emulation.md) for details.

## Physical Pointers

There are a few drivers available for supported physical pointing devices integrated into ZMK powered device. When doing so, you can use your device as both a keyboard and a pointing device with any connected hosts. The functionality can be extended further, e.g. slow mode, scroll mode, temporary mouse layers, etc. by configuring input processors linked to the physical pointing device.

## Input Processors

Input processors are small pieces of functionality that process and optionally modify events generated from emulated and physical pointing devices. Processors can do things like scaling movement values to make them larger or smaller for detailed work, swapping the event types to turn movements into scroll events, or temporarily enabling an extra layer while the pointer is in use.

## Input Listeners

Listeners are the key piece that integrate the low level input devices to the rest of the ZMK system. In particular, listeners subscribe to input events from the linked device, and when a given event occurs (e.g. X/Y movement), apply any input processors before sending those events to the HID system for notification to the host. The main way to modify the way a pointer behaves is by configuring the input processors for a given listener.