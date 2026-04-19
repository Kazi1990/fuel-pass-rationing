# fuel-pass-rationing
# Fuel Pass Pro | Intelligent Rationing Hub 🚗⛽

A sleek, premium, and efficient web application designed to streamline fuel rationing management. Developed for the **SBAC Hasnabad Hub**, Powered by **ICT Eng.**

This application leverages modern web technologies and a serverless backend to provide real-time fuel quota tracking, secure dispenser interfaces, and a robust admin console. No more manual logs or data discrepancies!

---

## 🌟 Key Features

The application is structured into three distinct, high-tech modules, each with its own visual theme and functionality.

### 1. User Portal (Cyan Theme)
Dedicated to vehicle owners for easy onboarding and status checks.
* **Account Activation:** Register new vehicles with full owner details and vehicle ID.
* **View Status:** Instantly check current fuel quota and generate a unique QR code for verification at the pump.

### 2. Pump Terminal (Pink Theme)
Designed for dispenser operators for quick and secure fuel allocation.
* **QR Code Scanner:** Scan user-generated QR codes to instantly verify account details.
* **Real-time Verification:** Displays verified owner name and vehicle ID.
* **Secure Dispensing:** Input fuel quantity and dispense with real-time quota updates. Prevents allocation beyond the remaining quota.

### 3. Admin Center (Purple Theme)
A comprehensive command center for system administrators.
* **Secure Authentication:** Protected by a dedicated access key.
* **Live Data Feed:** Monitor CPU load, active passes, and recent transactions.
* **Core Database Management:** View and manage all registered vehicles and their quotas.
* **Weekly Reset:** Easily reset all vehicle quotas to the standard allowance (e.g., 60L) with a single click.

---

## 🚀 Getting Started

To get a local copy up and running, follow these simple steps.

### Prerequisites
* A modern web browser (e.g., Chrome, Firefox, Safari).
* A basic understanding of HTML, CSS, and JavaScript.

### Installation & Firebase Setup

This project uses **Firebase Firestore** as its serverless database. You'll need to set up your own Firebase project to make it work.

1.  **Clone the Repository:**
    ```bash
    git clone [https://github.com/your-username/Fuel-Pass-Pro.git](https://github.com/your-username/Fuel-Pass-Pro.git)
    cd Fuel-Pass-Pro
    ```

2.  **Firebase Project Setup:**
    * Go to the(https://console.firebase.google.com/).
    * Create a new project named `Fuel Pass Pro` (or similar).
    * In the project overview, click the "Web" icon (`</>`) to add a new web app. Name it and click "Register app."
    * Firebase will provide your `firebaseConfig` object. **Copy this.**

3.  **Configure Firestore Database:**
    * In the Firebase console sidebar, click on "Firestore Database."
    * Click "Create database." Choose your location and start in **test mode** (for development).
    * **Crucial Rule Set:** Go to the "Rules" tab. Your `security rules` should allow read/write access to authenticated users or, during development in test mode, everyone. *For production, always implement strong security rules.* An example for development:
        ```javascript
        rules_version = '2';
        service cloud.firestore {
          match /databases/{database}/documents {
            match /{document=**} {
              allow read, write: if true; // Only for test mode!
            }
          }
        }
        ```
    * **Database Structure:** You don't need to manually create collections. The app will create the `vehicles` collection and add documents (by vehicle ID) with `owner_name`, `remaining_quota`, and `last_active` fields.

4.  **Update `index.html`:**
    * Open `index.html` in your code editor.
    * Find the `<script type="module">` section at the bottom.
    * Locate the `firebaseConfig` object and replace it with your copied config:
        ```javascript
        const firebaseConfig = {
            apiKey: "YOUR_API_KEY",
            authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
            projectId: "YOUR_PROJECT_ID",
            storageBucket: "YOUR_PROJECT_ID.appspot.com",
            messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
            appId: "YOUR_APP_ID"
        };
        ```

5.  **Run the App:**
    * Open `index.html` directly in your browser, or use a local live server (e.g., VS Code Live Server extension).
    * Navigate to `Admin Center`, log in with the default key `1234`, and populate some test data using `Account Activation`.

---

## 💻 Tech Stack

* **HTML5 & CSS3:** For structuring and advanced glass-morphism styling.
* **JavaScript (ES6+):** For application logic and real-time database interaction.
* **Firebase Firestore:** NoSQL serverless database for secure and instant data synchronization.
* **Tailwind CSS:** For rapid, responsive, and utility-first UI development.
* **Orbitron & Rajdhani Fonts:** For the high-tech, futuristic typography.
* **QRCode.js:** For generating unique QR codes on demand.

---

## ⚙️ Administration

The Admin Console is your core system management tool.

* **Access:** The console is locked. Use the defined access key to unlock it.
* **Reset Quotas:** In the `Admin Command Center`, click the `WEEKLY RESET` button. This is designed as a weekly task to reset all vehicle quotas to the standard level. It prompts for confirmation to prevent accidental resets.

---

## 📜 License

This project is open-source and available under the **ICT Eng.** internal use license.

---

<div align="center">
  <img src="https://via.placeholder.com/150x150.png?text=ICT+Eng." alt="ICT Eng. Logo" />
</div>
