# PGDAV College Student Attendance System

A QR-based student attendance system for PGDAV College (University of Delhi), built as the Software Engineering project for CS(H) V Semester, 2026.

The professor starts a class session and a QR code appears. The code changes every 30 seconds, so students must scan it in the classroom to be marked present. A shared photo of the QR stops working almost immediately.

## Live demo

After you enable GitHub Pages (see below), the demo is at:

`https://<your-github-username>.github.io/<repo-name>/`

## Install as an app

The project is a Progressive Web App (PWA), so it installs like a normal app and opens full-screen with its own icon.

- **Android (Chrome):** open the live link, tap the three dots, then **Install app** (or use the **Install app** button on the front page).
- **iPhone (Safari):** open the link, tap Share, then **Add to Home Screen**.
- **Windows or Mac (Chrome or Edge):** click the install icon in the address bar.
- **Android APK:** paste the live link into [PWABuilder](https://www.pwabuilder.com), choose Android, and download the package.

The app caches itself after the first visit, so it opens even with a poor connection.

## Features

- Role-based login for Professor, Student and Admin
- Dynamic QR code with a 30-second token and a countdown timer
- Scan validation: expired token, tampered token, duplicate scan and closed session are all rejected
- Three subjects, each with its own sessions and reports
- Student view with subject-wise attendance and a warning below 75%
- Professor can correct attendance manually, and every change is logged
- Admin can add students and view the audit log
- Reports with a class average, defaulter list and CSV export
- Login lockout for 30 seconds after 3 wrong attempts, and automatic logout after 10 minutes of inactivity

## Demo accounts

| Role | Username | Password |
|---|---|---|
| Professor | `prof` | `prof123` |
| Admin | `admin` | `admin123` |
| Student (roll 1 to 20) | `1` to `20` (or full name) | `stud1` to `stud20` |

These are demo-only credentials.

## Tech

HTML, CSS and JavaScript in a single file (`index.html`). QR codes are generated with [qrcodejs](https://github.com/davidshimjs/qrcodejs). All data is in memory and resets when the page reloads.

## Security tests covered

| Test | What it checks |
|---|---|
| Replay of an expired QR | The old token is rejected |
| Tampered token | An invalid token is rejected |
| Duplicate scan | A second scan in one session is rejected |
| Brute-force login | The account locks after 3 failed attempts |
| Role-based access | A student sees only their own attendance |

The full SRS (requirements, DFD, ERD, test cases and the SQL injection, XSS and authentication testing plan) is in the `docs/` folder.

## Planned: full backend

A Flask and SQLite version with a real database, hashed passwords, parameterized queries and output encoding, to be tested with OWASP ZAP and Burp Suite.

## Team

- Shashank Roy (Roll no. 1)
- [Add teammates here]

Submitted to: Prof. Chamoli Akshay

## License

MIT
