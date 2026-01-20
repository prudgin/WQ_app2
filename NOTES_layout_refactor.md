# Layout Refactor Notes

## Editable layout source
- Unpacked YAML lives under `msapp_src/`, with screen definitions in `msapp_src/Src\\scrHome.pa.yaml`, `msapp_src/Src\\scrNewReading.pa.yaml`, and `msapp_src/Src\\scrReview.pa.yaml`.
- The updated packaged app is `Microsoft.PowerApps/apps/16283016894094406944/Naed874ae-b95d-42b1-998e-d10396040d12-document.msapp`.

## Screens rebuilt
- **scrHome**: Rebuilt with a new AutoLayout hierarchy using a responsive nav rail/top bar and a centered farm-selection card. Navigation buttons are now container-driven with no absolute positioning.
- **scrNewReading**: Rebuilt from scratch into a header, scrollable body, and footer. The body wraps three card containers (meta + parameters) with per-row AutoLayout, removing the old manual positioning.
- **scrReview**: Added a matching AutoLayout shell with a responsive nav and placeholder content.

## Responsive behavior (validation)
- **Narrow (App.Width ~700)**: Home nav becomes a horizontal top bar with two equal-width buttons; main card stays centered and readable. New Reading cards stack vertically (A, then B, then C), with footer notes row spanning full width.
- **Medium (App.Width ~900–1100)**: New Reading card wrap stabilizes with Region A on the left and Regions B/C wrapping to the right, maintaining consistent spacing and row alignment; Home nav remains horizontal at the top edge.
- **Wide (App.Width ~1300+)**: Home shows a left nav rail (~220px) with main content to the right; New Reading presents Regions A/B/C as three columns in a single row.

## Import back into Power Apps
1. Use the updated app package at `Microsoft.PowerApps/apps/16283016894094406944/Naed874ae-b95d-42b1-998e-d10396040d12-document.msapp`.
2. Import the .msapp into Power Apps Studio (File > Open > Browse) to verify the responsive layout.
