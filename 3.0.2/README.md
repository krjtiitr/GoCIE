# GoCIE 3.0.2

# **What's New**

## Overview

The latest GoCIE update introduces enhancements focused on CIE 1931
chromaticity analysis, color-gamut visualization, point annotation, and
spectral-point characterization. Existing plotting, printing, exporting,
copying, and other established GoCIE functions are retained.

## 1. Expanded Color Standards

The **Color Standard** menu now includes:

-   **sRGB**

![sRGB](https://github.com/krjtiitr/GoCIE/blob/main/images/GoCIE302_srgb_gamut.png?raw=true)

-   **Rec.709 (BT.709)**

![BT 709](https://github.com/krjtiitr/GoCIE/blob/main/images/GoCIE302_bt709_gamut.png?raw=true)

-   **Adobe RGB**

![Adobe RGB](https://github.com/krjtiitr/GoCIE/blob/main/images/GoCIE302_adobeRGB_gamut.png?raw=true)

-   **DCI-P3**

![DCI-P3](https://github.com/krjtiitr/GoCIE/blob/main/images/GoCIE302_dcip3_gamut.png?raw=true)

-   **BT.2020 (Rec.2020)**

![BT 2020](https://github.com/krjtiitr/GoCIE/blob/main/images/GoCIE302_bt2020_gamut.png?raw=true)

These are added alongside the existing EBU, NTSC, PAL/SECAM, and SMPTE
standards. Rec.709 (BT.709) and BT.2020 (Rec.2020) are listed together.

### CIE 1931 primary coordinates

| Color standard | Red (x, y) | Green (x, y) | Blue (x, y) |
| :--- | :--- | :--- | :--- |
| EBU | 0.640, 0.330 | 0.290, 0.600 | 0.150, 0.060 |
| NTSC | 0.670, 0.330 | 0.210, 0.710 | 0.140, 0.080 |
| PAL/SECAM | 0.640, 0.330 | 0.290, 0.600 | 0.150, 0.060 |
| SMPTE | 0.630, 0.340 | 0.310, 0.595 | 0.155, 0.070 |
| sRGB | 0.640, 0.330 | 0.300, 0.600 | 0.150, 0.060 |
| Rec.709 (BT.709) | 0.640, 0.330 | 0.300, 0.600 | 0.150, 0.060 |
| Adobe RGB | 0.640, 0.330 | 0.210, 0.710 | 0.150, 0.060 |
| DCI-P3 | 0.680, 0.320 | 0.265, 0.690 | 0.150, 0.060 |
| BT.2020 (Rec.2020) | 0.708, 0.292 | 0.170, 0.797 | 0.131, 0.046 |

**Note:** sRGB and Rec.709 have the same CIE 1931 primary
chromaticities, so their CIE 1931 gamut triangles are identical. Their
distinction is outside the xy primary triangle.

## 2. Custom Gamut Triangle

A new **Custom** option allows users to define an RGB gamut directly in
CIE 1931 xy coordinates.

Selecting **Custom** opens the **Custom Gamut Triangle** dialog, where
all six values are entered together:

``` text
             X:             Y:

Blue       [__________]   [__________]

Green      [__________]   [__________]

Red        [__________]   [__________]


             Accept       Cancel
```

The coordinates are validated before acceptance. Values must be within
the valid CIE 1931 coordinate range, and the three points must form a
non-degenerate triangle.

**Accept** applies the custom gamut; **Cancel** leaves the current gamut
unchanged.

## 3. Distance of a CIE Point from RGB Primaries

For each newly added CIE point, GoCIE calculates its Euclidean distance
in CIE 1931 xy space from the **Red, Green, and Blue primary points of
the currently selected color standard**:

$$
d = \sqrt{(x - x_p)^2 + (y - y_p)^2}
$$

The values are displayed in the status bar as:

`Standard: Distance to Red: ___, Green: ___, Blue: ___`

The calculation also works with a Custom gamut.

This provides a useful numerical descriptor for assessing how close a
spectral chromaticity point is to each primary of the selected display
gamut.

## 4. Distance Information in ASCII Copy

The distance information is included when CIE data are copied as ASCII
data, alongside the CIE X and Y coordinates:

-   Distance to Red
-   Distance to Green
-   Distance to Blue


| Label  | x  | y  | Distance_to_Red |  Distance_to_Green  | Distance_to_Blue |
| :--- | :--- | :--- | :--- | :--- | :--- |
BCF3IR450  |  0.5781850000 |  0.4207440000  |  0.1290909283  |  0.4682192091  |  0.5550788843
Sample2 |   0.6077550000 |   0.3879640000  |  0.0850544844 |   0.5117775155  |  0.5600326467



This makes the values directly available for spreadsheet, scripting,
statistical, and manuscript analysis.

## 5. Improved Point-to-Label Connector

The line connecting a CIE point to its attached label has been enhanced.

The connector now has:

-   Configurable **color**
-   Configurable **line width**
-   A default line width consistent with the wavelength-label tick line
    width

The connector styling is independent of the point-marker color.

## 6. Label Connector Settings in Manage Points

The point-management interface provides control over:

-   **Label line color**
-   **Label line width**

These properties are associated with the individual CIE point.

## 7. Progressive Marker Shapes

New CIE points progressively use the available marker shapes instead of
always receiving the same shape.

For example:

``` text
1st point  → Filled Circle
2nd point  → Filled Square
3rd point  → Filled Triangle
4th point  → Filled Star
5th point  → Filled Inverted Triangle
...
```

The sequence cycles when the available shapes are exhausted. The marker
can still be changed manually through point management.

## 8. Improved Automatic Label Placement

New points now receive proper initial label-offset values.

This fixes the earlier problem where newly created labels could appear
at the lower-left corner of the plot and label dragging could become
restricted.

The correction applies to points introduced through operations such as:

-   Add Point
-   Open Spectrum
-   Drag-and-drop spectrum
-   Point-management operations

**Show Labels as List** remains unchanged.

# Summary

The current enhancement adds:

1.  Five modern color standards.
2.  A six-coordinate Custom Gamut editor.
3.  CIE 1931 distance from each RGB primary.
4.  Distance information in ASCII data copying.
5.  Configurable point-to-label connector color.
6.  Configurable point-to-label connector width.
7.  Progressive marker shapes for newly added points.
8.  Improved automatic label placement.

These additions extend GoCIE's usefulness for modern OLED and
organic-emitter research while retaining the established GoCIE plotting
and data-handling workflow.
