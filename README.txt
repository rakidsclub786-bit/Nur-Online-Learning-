NUR ONLINE LEARNING — FREE WEBSITE STARTER
==========================================

This customized website is for:
- School classes (Classes 1–12)
- Competitive exam preparation
- English, Hindi and Assamese interface (use the language selector)
- Student registration/login using Firebase Authentication
- Student profile storage in Firestore
- Sample Google Meet buttons

IMPORTANT: These files are a starter website, not a live hosted website. Real online registration starts only after you configure Firebase. Live-class buttons are examples and must be replaced with your actual meeting URLs.

PART 1 — SET UP REAL STUDENT ACCOUNTS
-------------------------------------
1. Open https://console.firebase.google.com/ and sign in with a Google account.
2. Choose Create a project. Name it "Nur Online Learning".
3. In Project Overview, click the Web icon (</>) to register a web app.
4. Copy the Firebase web config values shown.
5. Open index.html in a text editor.
6. Near the bottom, find the firebaseConfig object and replace:
   PASTE_YOUR_FIREBASE_API_KEY
   PASTE_YOUR_PROJECT.firebaseapp.com
   PASTE_YOUR_PROJECT_ID
   PASTE_YOUR_FIREBASE_APP_ID
   with the matching values from your Firebase config. Keep the quotes and commas.
7. Firebase Console > Build > Authentication > Get started.
8. Under Sign-in method, enable Email/Password.
9. Firebase Console > Build > Firestore Database > Create database.
10. Open Firestore Database > Rules and use the starter rules below.
11. Publish the updated index.html as described in Part 2.

STARTER FIRESTORE SECURITY RULES
--------------------------------
These allow a signed-in student to access only their own profile document.
They do not implement teacher/admin tools.

rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /students/{userId} {
      allow create, read, update: if request.auth != null
                                  && request.auth.uid == userId;
      allow delete: if false;
    }
  }
}

PART 2 — PUBLISH FOR FREE WITH GITHUB PAGES
-------------------------------------------
1. Create/sign in at https://github.com/
2. Create a new public repository named "nur-online-learning".
3. Upload index.html to the top/root of that repository.
4. Open repository Settings > Pages.
5. Under Build and deployment, choose "Deploy from a branch".
6. Select branch "main" and folder "/ (root)", then Save.
7. Wait for GitHub Pages to publish the site. The URL will look like:
   https://YOUR-GITHUB-USERNAME.github.io/nur-online-learning/
   Replace YOUR-GITHUB-USERNAME with your actual GitHub username.
8. Open the link on your phone to test it.

PART 3 — ADD YOUR OWN LIVE CLASS LINKS
--------------------------------------
1. Create a class meeting at https://meet.google.com/
2. Copy the real meeting URL.
3. Open index.html and search for href="https://meet.google.com/".
4. Replace each sample URL with the meeting link for that class.
5. Upload the updated index.html to GitHub again.

PART 4 — CHANGE COURSE DETAILS
------------------------------
In index.html, edit the course cards and class names. The language selector currently translates the main navigation, key headings, course summaries, registration labels and class section. Add your own contact details in the footer.

FREE PLAN NOTES
---------------
- GitHub Pages can host a static website at no hosting charge, subject to GitHub's current terms.
- Firebase has a no-cost tier and usage limits that can change.
- A public GitHub repository means the HTML source is visible. Never place passwords, private keys, or admin secrets in index.html.
- Firebase web configuration is intended to be included in a client app; protect all database data with correct Firebase Security Rules.
- Public Google Meet links may be shared by anyone who sees them. Share with enrolled students appropriately.
- This starter does not yet include a protected admin dashboard, class enrollment controls, attendance, quizzes, payments, or video hosting.
- If children use the site, collect only necessary data and follow applicable privacy and parental-consent requirements.
