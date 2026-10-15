# JaVeR Studio — Discord Rich Presence

**JaVeR Studio** is an independent project built around a custom Discord Rich Presence identity. It is intended to give an activity a distinct name, visual identity, and configurable status information on a Discord profile.

> **What this repository contains:** public legal and project-information pages for JaVeR Studio. It does **not** contain a standalone desktop application or an RPC client.

[Terms of Service](terms.html) · [Privacy Policy](privacy.html) · [Русская версия](README.ru.md)

## How it works

Discord Rich Presence is an integration between an application running on a user's device and the Discord client. The JaVeR Studio Application ID identifies the application configuration in the Discord Developer Portal; the ID alone does not run software or publish an activity.

The intended flow is:

1. **Application setup.** JaVeR Studio is registered in the Discord Developer Portal. Its Application ID identifies the project, and any artwork used by the activity is configured as an application asset.
2. **Local RPC client.** A compatible RPC client runs on the user's computer. The client supplies the activity information, such as the details and state text, timestamps, and the asset keys it wants to display.
3. **Local connection to Discord.** The RPC client communicates with the running Discord desktop client through Discord's local RPC interface. In the native desktop integration, this communication uses inter-process communication (IPC).
4. **Activity display.** Discord renders the activity using the information provided by the client and the assets associated with the Application ID. Whether other people can see the activity also depends on Discord's activity and privacy settings.
5. **Stopping the activity.** When the RPC client stops sending or clears the activity, the custom presence is no longer maintained.

A compatible RPC client is therefore required. Renaming the application in the Developer Portal changes its configured identity; it does not create or install that client. This repository does not provide one.

## Repository contents

| File | Purpose |
| --- | --- |
| `index.html` | Landing page linking to the legal documents |
| `terms.html` | Terms of Service |
| `privacy.html` | Privacy Policy |
| `README.md` | Project overview and technical explanation (English) |
| `README.ru.md` | Russian version of this README |

## Privacy and data handling

This repository is a static website. Its HTML pages do not implement a user account system, an application backend, or analytics.

In the intended Rich Presence setup, activity fields are sent by the local RPC client to Discord so Discord can display them. Discord handles that information under its own policies. Any separate RPC client may have its own permissions, logs, telemetry, or data practices; those are not controlled by this repository and should be reviewed independently.

The Privacy Policy is accurate only while JaVeR Studio does not operate a backend or independently collect or store personal information. If that changes, update the policy before deploying the change.

## Publish the legal pages with GitHub Pages

1. Create a **public** GitHub repository, for example `javer-studio-legal`.
2. Upload `index.html`, `terms.html`, and `privacy.html` to the repository root.
3. Open **Settings → Pages**.
4. Under **Build and deployment**, select **Deploy from a branch**, choose the `main` branch and the `/(root)` folder, then save.
5. Once deployment is complete, verify that the landing page and both legal documents open publicly without signing in.
6. Add the published document URLs to the matching fields in Discord Developer Portal → **General Information**.

The URLs will follow this pattern (replace `YOUR-GITHUB-USERNAME` with your GitHub username):

- `https://YOUR-GITHUB-USERNAME.github.io/javer-studio-legal/`
- `https://YOUR-GITHUB-USERNAME.github.io/javer-studio-legal/terms.html`
- `https://YOUR-GITHUB-USERNAME.github.io/javer-studio-legal/privacy.html`

## Official documentation

- [Discord Rich Presence overview](https://discord.com/developers/docs/rich-presence/overview)
- [Discord RPC documentation](https://discord.com/developers/docs/topics/rpc)
- [Discord Privacy Policy](https://discord.com/privacy)

## Disclaimer

JaVeR Studio is an independent project and is not affiliated with, sponsored by, or endorsed by Discord Inc. Discord and its logos are trademarks of their respective owners.

The documentation in this repository describes the intended configuration. Keep it consistent with the actual software and services you use. The legal pages are practical project documents, not legal advice.
