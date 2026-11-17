# Security Policy

## Reporting a vulnerability

Please **do not** open a public issue containing an API key, a real name, or a full private journal entry.

If the repository has **Security → Report a vulnerability** enabled, use that private channel.  
If not, open a minimal public issue saying that you would like to report a security problem, without including secrets or exploitable details.

## Scope

This is a static, client-side page. It has no backend, no accounts, and no project-owned API key.

Relevant security topics:

- exposure or redirection of a user-supplied DeepSeek API key
- XSS or unsafe HTML injection in user content or model output
- unintended network requests or third-party scripts
- CSP bypasses
- data persistence or deletion problems
- unsafe crisis handling

## Design boundaries

- API endpoint is fixed to `https://api.deepseek.com` in the page.
- CSP restricts `connect-src` to the same origin.
- API keys are stored in `sessionStorage` by default; `localStorage` only after explicit opt-in.
- Exported JSON excludes the API key.
- No analytics, ads, or external scripts are included.

## What is not a vulnerability

- The page source is public and can be copied or modified by anyone.
- A user can read or modify their own browser storage or network requests.
- A user can fork the project and change the code.
- Client-side code cannot fully protect a key from the device owner or browser extensions.
- DeepSeek API availability, pricing, or model behavior are outside this project's control.
