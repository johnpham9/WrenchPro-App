# WrenchPro

WrenchPro is a native, offline-first iOS and iPadOS field app for independent HVAC technicians. It combines a field notebook, customer and equipment history, service reports, lightweight invoicing, diagnostic tools, and truck stock tracking without the overhead of enterprise dispatch software.

## Highlights

- Jobs dashboard with recent, unpaid, and follow-up filters
- Customer directory with contact details, site notes, equipment, and service history
- Equipment profiles for residential and commercial HVAC systems
- Fast service visit entry with optional HVAC readings and refrigerant logs
- Reading comparisons against previous visits
- Equipment service timelines and callback risk flags
- Customer-friendly report phrases and callback closeout workflow
- Before-and-after service photos and customer signature capture
- PDF service report generation with the native iOS share sheet
- Lightweight invoices and estimates with labor, parts, tax, discount, and payment status
- HVAC calculators and reusable diagnostic checklists
- Truck stock mini inventory with reorder indicators
- English and Spanish interface options
- Offline SwiftData storage with private iCloud/CloudKit synchronization
- Light and dark mode support

## Technology

- SwiftUI-first interface
- SwiftData persistence
- CloudKit private database sync
- PhotosUI and UIKit camera integration
- Native PDF rendering and share sheet
- String Catalog localization
- No backend, account system, advertising SDK, or analytics SDK

## Requirements

- Xcode with support for the iOS 17.6 SDK or later
- iOS/iPadOS 17.6 or later
- An Apple Developer account and iCloud container access for device builds using CloudKit

The app supports both iPhone and iPad. Simulator builds use local SwiftData storage without CloudKit; physical-device builds use the private iCloud container configured by the project.

## Open And Run

1. Open `WrenchPro.xcodeproj` in Xcode.
2. Select the `WrenchPro` target.
3. In **Signing & Capabilities**, choose your development team.
4. Confirm that **iCloud** and **CloudKit** are enabled.
5. Select an iPhone or iPad simulator, or a signed physical device.
6. Build and run with **Product > Run**.

```sh
open WrenchPro.xcodeproj
```

## Command-Line Build

Run a simulator build from the project root:

```sh
xcodebuild \
  -project WrenchPro.xcodeproj \
  -scheme WrenchPro \
  -destination 'generic/platform=iOS Simulator' \
  build
```

## iCloud Configuration

The app currently references this CloudKit container:

```text
iCloud.com.johnpham.WrenchPro
```

Before distributing the app:

1. Register the app identifier and iCloud container in the Apple Developer portal.
2. Ensure the provisioning profile contains the iCloud and CloudKit entitlements.
3. Confirm that the container is assigned to the WrenchPro target.
4. Test synchronization between two physical devices signed into the same Apple Account.
5. Deploy the CloudKit schema to the production environment before App Store release.

If the bundle identifier or developer team changes, update the target capabilities, entitlements, and `WrenchProCloud.containerIdentifier` together.

## Project Structure

```text
WrenchPro/
|- App/            App entry point and model container
|- Models/         SwiftData models, sample data, and field insights
|- Resources/      Asset catalog and localized strings
|- Views/          Jobs, customers, equipment, reports, tools, and shared UI
|- Info.plist      Application configuration
`- WrenchPro.entitlements
```

## Data And Privacy

WrenchPro stores working data on the device and synchronizes it through the user's private iCloud database when iCloud is available. The app has no developer-operated backend and does not include advertising, cross-app tracking, or third-party analytics.

Photos and signatures are stored with service visit records. Generated PDF reports leave the app only when the user chooses a destination through the native share sheet.

See [PRIVACY.md](PRIVACY.md) for the complete privacy policy.

## Current Scope

WrenchPro is designed for a solo technician. It does not currently include:

- Multi-technician dispatching
- Route optimization
- Payment processing
- QuickBooks or accounting integrations
- Web or Android clients
- A developer-operated cloud service

Potential future extensions include branded report templates, Face ID app locking, voice-to-report summaries, compliance CSV exports, and maintenance reminders.

