---
title: Input Processor Overview
sidebar_label: Overview
---

# Input Processors Overview

"Input processors" are small pieces of functionality that process and optionally modify events generated from emulated and physical pointing devices. Processors can do things like scaling movement values to make them larger or smaller for detailed work, swapping the event types to turn movements into scroll events, or temporarily enabling an extra layer while the pointer is in use.

Below is a summary of pre-defined input processors and user-definable input processors available in ZMK, with references to documentation pages describing them.

## Pre-Defined

A set of predefined input processors is available by adding the following at the top of your keymap/overlay file:

```
#include <input/processors.dtsi>
```

Once included, you can use the following:

| Binding                    | Behavior                                     | Description                                                         |
| -------------------------- | -------------------------------------------- | ------------------------------------------------------------------- |
| `&zip_xy_scaler`           | [XY Scaler](scaler.md#pre-defined-instances) | Scale a the X/Y input events using a multiplier and divisor         |
| `&zip_x_scaler`            | [X Scaler](scaler.md#pre-defined-instances)  | Scale a the X input events using a multiplier and divisor           |
| `&zip_y_scaler`            | [Y Scaler](scaler.md#pre-defined-instances)  | Scale a the Y input events using a multiplier and divisor           |
| `&zip_xy_transform`        | [XY Transform](transformer.md)               | Transform X/Y values, e.g. inverting or swapping                    |
| `&zip_scroll_transform`    | [Scroll Transform](transformer.md)           | Transform wheel/horizontal wheel values, e.g. inverting or swapping |
| `&zip_xy_to_scroll_mapper` | [XY To Scroll Mapper](code-mapper.md)        | Map X/Y values to scroll wheel/horizontal wheel events              |
| `&zip_xy_swap_mapper`      | [XY Swap Mapper](code-mapper.md)             | Swap X/Y values                                                     |
| `&zip_temp_layer`          | [Temporary Layer](temp-layer.md)             | Temporarily enable a layer during pointer use                       |

## Used-Defined

Several of the input processors that have predefined instances, e.g. `&zip_xy_scaler` or `&zip_xy_to_scroll_mapper` can also have new instances created with custom properties around which input codes to scale, or which codes to map, etc.
