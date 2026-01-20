# Layout Refactor Notes

## Repository structure
- `manifest.json`
- `Microsoft.PowerApps/apps/16283016894094406944/`
  - `16283016894094406944.json` (app definition metadata and screen/control structure)
  - `N391b1d52-7a36-4f0d-b932-d9a7eef06bcf-identity.json`
  - `N555ce843-9d93-44fd-a921-3ad2f47b5da7-document.msapp`
  - `N8a2fb3d7-cfd6-45ed-8262-75270e066e15-logoSmallFile`

## Screen/control source mapping
- `Microsoft.PowerApps/apps/16283016894094406944/N555ce843-9d93-44fd-a921-3ad2f47b5da7-document.msapp` contains the packaged canvas app.
- Extracted text-based canvas source is now available under `msapp_src/` (e.g., `msapp_src/Src\\scrHome.pa.yaml`).

## Edit strategy
- Edit the unpacked `.pa.yaml` files in `msapp_src/Src\\` for screen/control layout updates.
- Preserve existing control names and formulas, updating only layout-related properties and Parent-relative references as required.

## Planned scope
- Refactor `scrHome`, `scrNewReading`, and `scrReview` (if present) to use responsive containers.
- Add/adjust AutoLayout containers, wrap rules, and padding/gap tokens (8/16/24).

## Changes applied
- Extracted canvas source from the `.msapp` package into `msapp_src/` to enable layout edits.
- Refactored `scrHome` into AutoLayout containers with a responsive nav rail/top bar and centered card.
- Refactored `scrNewReading` into header/body/footer containers with wrapping cards for meta/actions and parameter regions, plus a notes footer.
- Added a simple responsive layout for `scrReview` with navigation and a centered card.

## Repackaging steps
- After editing files under `msapp_src/`, repackage them back into `Microsoft.PowerApps/apps/16283016894094406944/N555ce843-9d93-44fd-a921-3ad2f47b5da7-document.msapp`.

## Sanity checklist
- Narrow width: nav becomes horizontal bar, cards stack vertically.
- Medium width: meta card and one parameter card in a row; remaining card wraps below.
- Wide width: three cards appear in a row; nav rail fixed width.

## Known fixed-position elements
- No major layout relies on fixed X/Y; AutoLayout containers handle structure. Hidden placeholder ButtonCanvas4_2 remains but is not visible.
