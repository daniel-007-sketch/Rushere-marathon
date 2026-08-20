# Rushere Marathon — Mobile Screen Notes

This document is the mobile implementation and testing reference for `RUSHERE RUN.html`. Keep it updated whenever the page structure, responsive CSS, media, buttons, or popups change.

## Viewport and page sizing

- The page uses `width=device-width, initial-scale=1` for correct rendering on phones.
- Panels are mobile-first and use fluid dimensions rather than fixed desktop widths.
- At widths up to `520px`, normal panels use a minimum height of `52svh`.
- The opening GIF panel remains `100svh` so it fills the visible phone screen.
- `svh` accounts for mobile browser controls more reliably than traditional `100vh`.

## Responsive breakpoint

The primary phone breakpoint is:

```css
@media (max-width: 520px)
```

At this breakpoint:

- Countdown spacing is reduced.
- The opening panel remains full-screen.
- Route action buttons change from two columns to one column.
- Popup padding is reduced to preserve usable space on narrow screens.

Desktop-specific presentation changes begin at `521px` and `700px`. Avoid adding overlapping breakpoints unless a component genuinely needs one.

## Fluid layout and typography

- Headings, body copy, spacing, and decorative elements use `clamp()` so they scale smoothly between phone and desktop sizes.
- Content widths use `min()` and percentage widths to prevent horizontal overflow.
- Images use responsive widths and retain their aspect ratio.
- The Route Maps and Marathon Photos content remains centered with narrow readable line lengths.

## Route Maps on mobile

- Each race distance is presented as an expandable `<details>` card.
- On phones, “View Map” and “Download Map” stack vertically for easier tapping.
- Both buttons currently open a modal containing: **Map to be Uploaded Soon**.
- The modal title reflects the selected distance.
- Users can close the modal with the “Back to routes” button, by tapping the backdrop, or by pressing Escape on a connected keyboard.

## Marathon Photos on mobile

- The “Access Photos” button currently opens an on-page modal instead of Google Drive.
- The modal displays: **Photos wil appear on the event day**.
- Users can close it with the “Back to photos” button, by tapping the backdrop, or by pressing Escape.

## Touch controls

- Interactive controls should retain a minimum touch height of approximately `44px`.
- Buttons use `touch-action: manipulation` for responsive taps.
- Hover-only styles are contained in `@media (hover: hover)` so they do not remain stuck after touchscreen taps.
- Do not place important controls too close to the screen edge or to each other.

## Media

- The opening visual should cover the viewport without producing horizontal scrolling.
- Large media assets should be compressed before publishing to reduce loading time on mobile data.

## Accessibility

- Popups use `role="dialog"`, `aria-modal="true"`, labelled headings, and `aria-hidden` state changes.
- Focus moves to the popup’s back button when opened and returns to the triggering control when closed.
- Escape closes either popup.
- `prefers-reduced-motion: reduce` minimizes animations and transitions.
- Maintain readable color contrast and do not communicate essential information through color alone.
- Preserve visible keyboard focus indicators on links, buttons, and expandable route cards.

## Mobile test checklist

- [ ] Test at 320px, 375px, 390px, 430px, and 520px widths.
- [ ] Confirm there is no horizontal scrolling.
- [ ] Confirm the opening GIF fills the visible screen.
- [ ] Confirm headings and body text remain readable without zooming.
- [ ] Confirm every route card expands and collapses correctly.
- [ ] Confirm both route buttons open the “Map to be Uploaded Soon” popup.
- [ ] Confirm the selected route distance appears in the popup title.
- [ ] Confirm the photos button opens its event-day popup and does not navigate to Google Drive.
- [ ] Confirm both popups fit on-screen in portrait and landscape orientations.
- [ ] Confirm popup backdrop taps, back buttons, and Escape close the correct popup.
- [ ] Confirm keyboard focus returns to the button that opened the popup.
- [ ] Confirm the page remains usable with reduced motion enabled.
- [ ] Test in iOS Safari and Chrome on Android.

## Maintenance rule

When changing the mobile design, verify the page at `520px` and `521px` to catch breakpoint jumps. Update this file whenever user-facing mobile behavior changes.
