# User Login with QR Code and Real-Time Photo Transfer

## Objective

1. Create a login system for a user on a desktop.
2. Display a unique QR code on the desktop after login.
3. When scanned using a mobile device:
   - Open the camera on the mobile device.
   - Allow the user to click a photo.
   - Display the captured photo on the desktop screen in real time.

---

## Features to Implement

1. **User Authentication**:
   - A simple login form with email and password.
   - Backend to validate and generate a session.

2. **QR Code Generation**:
   - Generate a QR code unique to the user session.
   - QR code should include a unique URL or token that links to the photo upload page on the mobile.

3. **Mobile Interaction**:
   - When the QR code is scanned, redirect to a mobile-friendly page with camera access.
   - Enable the user to capture a photo and upload it.

4. **Real-Time Photo Display**:
   - Use WebSocket or similar real-time technologies to push the uploaded photo to the desktop application.

5. **Database**:
   - Store user details, session tokens, and optionally, the photo metadata.

---

## Steps to Develop

### 1. Authentication System

- **Frontend**:
  - A React login form on the desktop.
- **Backend**:
  - Node.js API with user authentication using JWT.
  - Use MySQL to store user credentials.

---

### 2. QR Code Generation

- **Frontend**:
  - After login, generate a QR code using a library like `qrcode.react` or `qrcode-generator`.
  - Encode a unique URL (e.g., `https://yourserver.com/photo-upload?sessionToken=<uniqueToken>`).
- **Backend**:
  - Generate a session-specific token upon login.
  - Store this token in the database with an expiration time.

---

### 3. Mobile Interaction

- **Frontend**:
  - A React/React Native mobile-friendly page accessible via the QR code.
  - Use the browser’s camera access API (`navigator.mediaDevices.getUserMedia`) or React Native's camera libraries for mobile apps.
- **Backend**:
  - API endpoint to accept photo uploads.
  - Validate the session token from the QR code.

---

### 4. Real-Time Photo Display

- **Backend**:
  - Use WebSocket (e.g., `Socket.IO`) to enable real-time updates.
  - Notify the desktop application when a new photo is uploaded.
- **Frontend**:
  - The desktop React app should subscribe to WebSocket events.
  - Display the photo dynamically upon receiving it.

---

## Tech Stack

1. **Frontend**:
   - Desktop: React with WebSocket for real-time updates.
   - Mobile: React/React Native for camera access.

2. **Backend**:
   - Node.js and Express.js for REST APIs.
   - Socket.IO for WebSocket communication.

3. **Database**:
   - MySQL for storing user data, session tokens, and metadata.

4. **Others**:
   - QR Code: Use `qrcode` or similar npm package.
   - File Storage

---
