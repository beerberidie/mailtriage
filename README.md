# MailTriage

Smart email triage that runs entirely in your browser. No backend server. Works on GitHub Pages. Your data stays on your device.

## Deploy to GitHub Pages

1. Create a new repo on GitHub called `mailtriage`
2. Push this folder to it
3. Go to **Settings → Pages → Source: main branch / root**
4. Your app is live at `https://yourusername.github.io/mailtriage/`

## Connect Real Gmail (2 minutes)

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Click **Select a project → New Project** → name it `MailTriage` → Create
3. Go to **APIs & Services → Library** → search "Gmail" → Enable **Gmail API**
4. Go to **APIs & Services → Credentials → Create Credentials → OAuth client ID**
   - Application type: **Web application**
   - Name: `MailTriage`
   - Authorized JavaScript origins: add `https://yourusername.github.io`
   - Authorized redirect URIs: leave blank
5. Click **Create** → copy the **Client ID**
6. Open the app → paste the Client ID → click **Connect Gmail**

## Connect Real Outlook (2 minutes)

1. Go to [Azure Portal - App Registrations](https://portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade)
2. Click **New registration** → name it `MailTriage` → Accounts in any org → Register
3. Copy the **Application (client) ID**
4. Go to **Authentication → Add platform → Single-page application (SPA)**
   - Redirect URI: `https://yourusername.github.io/mailtriage/`
5. Click **Configure → Save**
6. Go to **API permissions → Add permission → Microsoft Graph → Delegated → Mail.Read, User.Read**
7. Open the app → paste the Client ID → click **Connect Outlook**

## How It Works

- OAuth2 gives the app read-only access to your inbox
- Emails are fetched via Gmail API or Microsoft Graph
- The Triage Engine categorizes every email using signal analysis:
  - Keyword detection (urgent, review, FYI, etc.)
  - Sender pattern matching (newsletters, noreply, etc.)
  - Subject line analysis (ALL CAPS, deadlines, etc.)
  - Contextual scoring with configurable sensitivity
- Results are cached in localStorage for offline access
- No data is ever sent anywhere except Google/Microsoft APIs

## Privacy

- **Read-only access** — the app cannot send, delete, or modify emails
- All processing happens in your browser
- Cached data stays in your device's localStorage
- Revoke access anytime in your Google/Microsoft account settings
