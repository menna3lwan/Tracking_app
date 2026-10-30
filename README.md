# Tracking App — Delivery Order Tracking

A Flutter mobile app for tracking delivery orders in real time, including driver location tracking, order status updates, and an authenticated customer/driver experience. Originally built as a team project; this repository is an independent, actively maintained continuation.

## Overview

Tracking App focuses on the last-mile delivery experience: customers and drivers authenticate, drivers' live location is tracked and shared, and order details/status are surfaced to the relevant parties in real time.

## My Role

I worked as a Flutter/mobile developer on the team that built this app, contributing to the mobile client within the Clean Architecture structure shared across the codebase. This repository is maintained independently going forward under my own account, with permission from the original team.

## Features

- Authentication (login, forgot/reset password)
- Live location tracking (driver location, distance calculation)
- Order details and status tracking
- Onboarding flow
- Image picking (e.g. for proof of delivery / profile)
- Localization (Arabic/English)
- Secure token storage with automatic refresh

## Tech Stack

- State management: `flutter_bloc`
- Dependency injection: `get_it` + `injectable`
- Networking: `dio` + `retrofit`, with interceptor-based logging and token refresh
- Secure storage: `flutter_secure_storage`
- Code generation: `freezed`, `json_serializable`, `build_runner`
- Routing: `go_router`
- Maps & location: `flutter_map`, `geolocator`, `latlong2`
- Media: `image_picker`, `cached_network_image`, `flutter_svg`, `lottie`
- Localization: `easy_localization`
- UI: `flutter_screenutil`, `shimmer`, `pinput`
- Testing: `flutter_test`, `mockito`, `bloc_test`

## Architecture

The app follows **Clean Architecture** with a **feature-first** folder structure:

```
lib/
├── app/             # Routing, app bootstrap
├── core/            # Shared infrastructure: DI, networking, errors, theme, widgets, services
└── features/
    ├── auth/
    ├── location_tracking/
    └── on_bording/
```

Each feature is split into `api` / `data` / `domain` / `presentation` layers, with BLoC/Cubit managing presentation state, repositories abstracting data sources, and dependency injection wiring it all together via `get_it` + `injectable`.

## Application Screenshots

Screens below are taken from the project's Figma design file and exported as PNG. They are grouped by the rider's journey through the app.

### Authentication

<table>
  <tr>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/01_onboarding.png" alt="Onboarding" width="200"><br><sub><b>Onboarding</b></sub></td>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/02_login.png" alt="Login" width="200"><br><sub><b>Login</b></sub></td>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/03_login_filled.png" alt="Login — filled" width="200"><br><sub><b>Login — filled</b></sub></td>
  </tr>
  <tr>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/04_login_email_error.png" alt="Login — email error" width="200"><br><sub><b>Login — email error</b></sub></td>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/05_login_password_error.png" alt="Login — password error" width="200"><br><sub><b>Login — password error</b></sub></td>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/06_forgot_password.png" alt="Forgot password" width="200"><br><sub><b>Forgot password</b></sub></td>
  </tr>
  <tr>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/07_forgot_password_email_error.png" alt="Forgot password — invalid email" width="200"><br><sub><b>Forgot password — invalid email</b></sub></td>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/08_verification_code.png" alt="Email verification" width="200"><br><sub><b>Email verification</b></sub></td>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/09_verification_code_error.png" alt="Email verification — invalid code" width="200"><br><sub><b>Email verification — invalid code</b></sub></td>
  </tr>
  <tr>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/10_set_new_password.png" alt="Set new password" width="200"><br><sub><b>Set new password</b></sub></td>
    <td width="33%"></td>
    <td width="33%"></td>
  </tr>
</table>

### Rider Application

<table>
  <tr>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/11_application_submitted.png" alt="Application submitted" width="200"><br><sub><b>Application submitted</b></sub></td>
    <td width="33%"></td>
    <td width="33%"></td>
  </tr>
</table>

### Delivery Flow

The rider's active delivery journey, in order: accept a request, navigate to the store, collect the order, navigate to the customer, and complete the delivery.

<table>
  <tr>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/12_home_incoming_orders.png" alt="Home — incoming requests" width="200"><br><sub><b>Home — incoming requests</b></sub></td>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/13_order_details_accepted.png" alt="Order details — accepted" width="200"><br><sub><b>Order details — accepted</b></sub></td>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/14_order_details_accepted_viewport.png" alt="Order details — accepted (viewport crop)" width="200"><br><sub><b>Order details — accepted (viewport crop)</b></sub></td>
  </tr>
  <tr>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/15_navigation_to_pickup.png" alt="Navigation — route to pickup" width="200"><br><sub><b>Navigation — route to pickup</b></sub></td>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/16_order_details_picked_up.png" alt="Order details — picked up" width="200"><br><sub><b>Order details — picked up</b></sub></td>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/17_navigation_to_customer.png" alt="Navigation — route to customer" width="200"><br><sub><b>Navigation — route to customer</b></sub></td>
  </tr>
  <tr>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/18_order_details_out_for_delivery.png" alt="Order details — out for delivery" width="200"><br><sub><b>Order details — out for delivery</b></sub></td>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/19_order_details_arrived.png" alt="Order details — arrived" width="200"><br><sub><b>Order details — arrived</b></sub></td>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/20_order_details_delivered.png" alt="Order details — delivered" width="200"><br><sub><b>Order details — delivered</b></sub></td>
  </tr>
  <tr>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/21_delivery_completed.png" alt="Delivery completed" width="200"><br><sub><b>Delivery completed</b></sub></td>
    <td width="33%"></td>
    <td width="33%"></td>
  </tr>
</table>

### Order History

<table>
  <tr>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/22_my_orders.png" alt="My orders" width="200"><br><sub><b>My orders</b></sub></td>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/23_order_details_completed.png" alt="Order details — completed (read-only)" width="200"><br><sub><b>Order details — completed (read-only)</b></sub></td>
    <td width="33%"></td>
  </tr>
</table>

### Account & Profile

<table>
  <tr>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/24_profile.png" alt="Profile" width="200"><br><sub><b>Profile</b></sub></td>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/25_edit_profile_personal.png" alt="Edit profile — personal details" width="200"><br><sub><b>Edit profile — personal details</b></sub></td>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/26_edit_profile_vehicle.png" alt="Edit profile — vehicle details" width="200"><br><sub><b>Edit profile — vehicle details</b></sub></td>
  </tr>
  <tr>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/27_change_password.png" alt="Change password" width="200"><br><sub><b>Change password</b></sub></td>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/28_change_password_error.png" alt="Change password — error" width="200"><br><sub><b>Change password — error</b></sub></td>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/29_logout_confirmation.png" alt="Profile — logout confirmation" width="200"><br><sub><b>Profile — logout confirmation</b></sub></td>
  </tr>
</table>

### Alternate Design Iteration

An earlier iteration of the same delivery flow kept in the design file. It embeds a collapsible map directly into the order-details screen, instead of the dedicated navigation screens used by the current flow above. The completion screen is shared with the current flow.

<table>
  <tr>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/30_alt_home.png" alt="Home — with availability toggle" width="200"><br><sub><b>Home — with availability toggle</b></sub></td>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/31_alt_order_request.png" alt="Order request — accept or reject" width="200"><br><sub><b>Order request — accept or reject</b></sub></td>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/32_alt_tracking_accepted.png" alt="Tracking — accepted" width="200"><br><sub><b>Tracking — accepted</b></sub></td>
  </tr>
  <tr>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/33_alt_tracking_picked_up.png" alt="Tracking — picked up" width="200"><br><sub><b>Tracking — picked up</b></sub></td>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/34_alt_tracking_picked_up_map.png" alt="Tracking — picked up (map expanded)" width="200"><br><sub><b>Tracking — picked up (map expanded)</b></sub></td>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/35_alt_tracking_out_for_delivery.png" alt="Tracking — out for delivery" width="200"><br><sub><b>Tracking — out for delivery</b></sub></td>
  </tr>
  <tr>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/36_alt_tracking_final_step.png" alt="Tracking — final step" width="200"><br><sub><b>Tracking — final step</b></sub></td>
    <td align="center" valign="top" width="33%"><img src="assets/screenshots/37_alt_tracking_delivered_map.png" alt="Tracking — delivered (map expanded)" width="200"><br><sub><b>Tracking — delivered (map expanded)</b></sub></td>
    <td width="33%"></td>
  </tr>
</table>

## Getting Started

### Prerequisites
- Flutter SDK (see `.metadata` for the pinned version)
- A `.env` file at the project root (see `pubspec.yaml` assets) for runtime configuration

### Setup

```bash
# Install Flutter dependencies
flutter pub get

# Generate code (DI, freezed, json_serializable, retrofit)
dart run build_runner build --delete-conflicting-outputs

# Run the app
flutter run
```

## Testing

```bash
flutter test
```

## Provenance

This app was originally developed collaboratively by a team (originally hosted at `joudysami/Tracking_app`). It is now maintained independently here with the original contributors' permission, as a standalone continuation of that work.
