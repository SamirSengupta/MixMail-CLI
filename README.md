# MixMail CLI

MixMail is a command-line Gmail assistant that lets you search, read, and summarize email using natural language. It runs as a local CLI, uses the Gmail API for mailbox access, and uses Cerebras for reasoning and summarization.

## What It Does

- Search Gmail with plain-English prompts
- Read full messages and conversation threads
- Summarize inbox results and threads
- Detect attachments
- Keep setup inside the CLI with guided commands

## Install

### Option 1: Install From A Wheel

If you have a built release file:

```powershell
pip install mixmail-1.0.0-py3-none-any.whl
```

### Option 2: Install From Source

```powershell
git clone https://github.com/SamirSengupta/MixMail-CLI.git
cd MixMail-CLI
pip install .
```

## Run

```powershell
mixmail
```

## First-Time Setup

MixMail can now be configured entirely inside the CLI.

After starting `mixmail`, run:

```text
/api_key
/mail_creds
```

### `/api_key`

Paste your Cerebras API key when prompted.

### `/mail_creds`

You can provide Google OAuth credentials in either of these ways:

1. Paste the full Google OAuth desktop-app JSON directly into the terminal.
2. Paste a path to the JSON file, for example:

```text
C:/Users/YourName/Downloads/client_secret.json
```

You can also use:

```text
file:C:/Users/YourName/Downloads/client_secret.json
```

### `/setup`

Shows the active MixMail config paths.

## Google Gmail Setup

To use MixMail with Gmail, you need a Google OAuth desktop-app credential.

1. Open Google Cloud Console.
2. Create or select a project.
3. Enable the Gmail API.
4. Create OAuth credentials for a Desktop app.
5. Download the client secret JSON file.
6. If your app is still in testing mode, add the Gmail account as a test user.

On first successful login, MixMail opens a browser for Gmail authorization and stores the token locally for future runs.

## Commands

| Command | Description |
|---------|-------------|
| `help` | Show usage help |
| `reset` | Clear conversation history |
| `/api_key` | Save the Cerebras API key interactively |
| `/mail_creds` | Paste or import Google OAuth credentials |
| `/setup` | Show the active config file locations |
| `quit` / `exit` | Exit MixMail |

## Example Prompts

```text
find emails from recruiters last week
show unread emails with attachments
summarize the latest thread from Amazon
list job interview emails from this month
find emails mentioning visa sponsorship
```

## Where MixMail Stores Config

For installed CLI usage, MixMail stores its config under the user profile:

```text
~/.mixmail/
```

That directory typically contains:

- `.env`
- `client_secret.json`
- `token.json`

## Important Note

MixMail currently runs locally on the client machine. That means the machine using MixMail still needs:

- A Cerebras API key
- Google OAuth client credentials
- A one-time Gmail login in the browser

This is normal for a local CLI that talks directly to external APIs. If you want a fully hosted experience like Claude Code or Gemini CLI, MixMail would need a backend service.

## Development

Install locally for development:

```powershell
pip install .
```

Build distributables:

```powershell
python -m pip install build
python -m build
```

This generates artifacts in `dist/`.

## License

Add a license file if you plan to distribute MixMail publicly.
