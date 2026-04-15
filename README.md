# TriviaNight

A real-time multiplayer trivia game hosted on GitHub Pages with Firebase Realtime Database. No backend required.

## Getting Started

**Host a game:** https://dehlia24.github.io/trivia-night/trivia_night_host_dashboard.html

**Browse active games:** https://dehlia24.github.io/trivia-night/trivia_night_games.html *(admin only)*

---

## How to Run a Game

### 1. Open the Host Dashboard
Go to the host dashboard link above. A unique 6-character game code is automatically generated and shown on screen.

### 2. Share the Join Link
Players can join by:
- Scanning the **QR code** displayed on the waiting screen
- Opening the **player URL** shown on screen directly
- Going to the [player page](https://dehlia24.github.io/trivia-night/trivia_night_player.html) and entering the game code manually

### 3. Build Your Question Bank
In the **Question Bank** panel on the right:
- Click **+ Add Question** to add questions (added to the top of the list)
- Fill in the question, answer, category, and point value for each
- Use the **📌 Pin** button to guarantee a question appears in the next game
- Pinned questions show a gold border and always get included regardless of used status
- Click **Clear pins** to unpin all

### 4. Use Templates (Optional)
Save sets of questions as named templates to reuse across sessions:
- Select a template from the dropdown to load its questions into the bank
- Click **Save as Template** to save the current question bank under a new name
- Templates are shared globally — any host can load them

### 5. Set Up the Game
- Give your game a name using the **Game Name** field on the waiting screen
- Choose how many questions to include per round
- Watch players appear in the **Player Lobby** as they join
- Use the **Kick** button to remove a player before the game starts

### 6. Start the Game
Click **Start Game**. Questions are served one at a time. Players submit answers on their devices and scores update in real time.

### 7. Advance Questions
Click **Next Question** after each question to move forward. The host dashboard shows all player responses and scores as they come in.

### 8. End the Game
When all questions are done the leaderboard is shown to all players. From the gameover screen you can:
- Click **Play Again** to start a new session with a fresh code
- Click **End Session** to close the session and clean up

---

## Player Experience

1. Open the player URL or scan the QR code
2. Enter your name and tap **Join Game**
3. Wait in the lobby until the host starts
4. Answer each question before the timer runs out
5. See your running score and final leaderboard at the end

**Rejoin support:** If you accidentally close the tab, reopening the player URL will offer to rejoin your existing session with your score intact.

---

## Session Manager (Admin)

The [Session Manager](https://dehlia24.github.io/trivia-night/trivia_night_games.html) shows all active and recent games in real time. It is locked to the `Dehlia24` GitHub account.

From here you can:
- See all live, waiting, and recently ended sessions
- Join any active session as a player
- **Remove** a session immediately (with confirmation)

Sessions automatically expire and are cleaned up 4 hours after ending.

---

## Tech Stack

| Layer | Tool |
|---|---|
| Hosting | GitHub Pages |
| Database | Firebase Realtime Database |
| Auth (admin) | Firebase Authentication + GitHub OAuth |
| QR codes | qrcodejs (client-side, no API) |
| Feedback | Formspree |

---

## Firebase Setup (for forks)

If you fork this repo, you'll need your own Firebase project:

1. Create a project at [console.firebase.google.com](https://console.firebase.google.com)
2. Enable **Realtime Database**
3. Enable **GitHub** as an Authentication provider (Authentication → Sign-in method)
   - Create a GitHub OAuth App at github.com/settings/developers
   - Set the callback URL to `https://<your-firebase-project>.firebaseapp.com/__/auth/handler`
4. Add your GitHub Pages domain to Firebase **Authorized Domains** (Authentication → Settings)
5. Replace the `firebaseConfig` object in all three HTML files with your own project's config
6. Update `ALLOWED_GITHUB_LOGIN` in `trivia_night_games.html` to your GitHub username
