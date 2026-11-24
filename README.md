# SHALA

Mobile-first browser prototype for a guided virtual try-on workflow. The current implementation is a client-side HTML, CSS, and JavaScript application.

## Current implementation

The application entry point is `index.html`, which loads `app-v2.js`. The current source includes:

- A multi-step onboarding and measurement flow
- Pose and studio selection
- A staged clothing, bag, shoes, and accessories workflow
- Browser-local state persistence using `localStorage`
- Media persistence through IndexedDB in `media-store.js`
- A camera-preview path using `navigator.mediaDevices.getUserMedia()`
- A reveal flow and saved-favorite state
- A generation adapter boundary in `generator.js`

## Important implementation limits

This repository should currently be evaluated as a prototype, not a production AI try-on service.

- `generator.js` defaults to `mockGenerator`. It produces a generated SVG placeholder; it does not call a real image-generation provider.
- The application calls the generation adapter and stores its returned media in IndexedDB, but a production provider is not configured in the reviewed source.
- Camera preview is attempted through the browser's camera API and depends on browser permission and a secure context. A working camera preview is not evidence of an integrated image-generation pipeline.
- Browser-local storage is not a server-backed account, synchronization, or backup system.
- The repository README previously referenced a design scope-lock document at the root. That file was not found at the expected path during this review; treat the source files as the current inspectable implementation until the design document is restored or its location is confirmed.
- Production accessibility, cross-browser behavior, privacy controls, and deployment behavior have not been independently verified in this audit.

## Project structure

- `index.html` — application entry point
- `app-v2.js` — application interface and workflow
- `generator.js` — generation provider interface and current mock implementation
- `media-store.js` — IndexedDB media storage helpers
- `styles.css` — application styling
- `assets/` — visual assets used by the interface

## Running locally

Serve the repository directory with a local HTTP development server and open the resulting local URL in a modern browser. Camera access generally requires localhost or HTTPS and explicit browser permission.

No package manager or build command is documented in the reviewed entry point. No automated test command was verified during this review.

## Status

**Prototype / development stage.** Do not represent this repository as a production AI try-on application until a real generation provider, privacy and data-handling controls, automated tests, and deployment verification are in place.
