SMART ATTENDANCE SYSTEM — FINAL PWA BUILD

Included
- Existing Smart Attendance interface retained
- Firebase Firestore cloud data sync
- PWA install support (Android/desktop + iPhone/iPad instructions)
- QR/share/copy app link
- Offline app shell caching
- Persistent login on the same browser/device
- One browser/device = one account lock
- Admin/Developer device release screen
- Password Management permissions:
  * Admin: Student + Faculty
  * Developer: Student + Faculty
  * Faculty: Student only
  * Student: cannot manage other users
- Existing passwords are never displayed
- Forgot Password / SMS OTP flow removed
- Department data is read from Firestore and is NOT recreated on every refresh

Firebase project
smart-attendance-system1-58089

Important Firestore collection
deviceLocks/{deviceId}
Stores the account assigned to a browser/device. The device ID is a random browser-local identifier, not a hardware ID. Clearing browser/site data, using another browser/profile, or another device can create a new ID. For true hardware-level enforcement, Firebase Authentication + trusted server-side enforcement is recommended.

Before publishing
1. Upload all files while preserving the folder structure.
2. Host over HTTPS (GitHub Pages, Firebase Hosting, etc.).
3. The QR code automatically uses the current HTTPS app URL.
4. If Firestore Security Rules are restrictive, allow the app's existing user/session model to read/write deviceLocks as required.
5. Do not expose service-account credentials in this client app.

Default demo admin (only created if users collection is empty)
Username: admin
Password: admin123
Change the default password after first login using an appropriate admin workflow.

Persistent login
The app stores only a session marker (user document ID + device ID) in browser storage; it does not store the login password in localStorage. Logout clears the session but intentionally does not release the device lock. Admin/Developer can release the lock from System & Cloud Database Management.
