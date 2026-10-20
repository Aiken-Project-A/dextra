# Dextra

*Dextra* is Latin for "right hand". It is a small personal command-line client for the
[YouTube Data API v3](https://developers.google.com/youtube/v3) that acts on its owner's
YouTube account from a terminal: rate videos, post comments and replies, manage
subscriptions and playlists.

It pairs with [yt-dlp](https://github.com/yt-dlp/yt-dlp): yt-dlp is the eyes (watch, read,
download), Dextra is the hand (act).

## Who it is for

Dextra was written for one person: the owner of this repository, using their own Google
account on their own computer. It is not a hosted service: there is no server, no
analytics and no telemetry. Anyone can read the code. If you use it, you create your own
OAuth client in your own Google Cloud project, and your data stays between your computer
and Google.

## What it can do

| Command | What it does | Quota units |
|---|---|---|
| `dextra auth` | sign in once through the browser | — |
| `dextra me` | show the channel of the signed-in account | 1 |
| `dextra like <video>`, `dislike`, `unlike` | rate a video or remove the rating | 50 + 1 |
| `dextra rating <video>…` | show your ratings of videos | 1 |
| `dextra comment <video> "text"` | post a comment | 50 |
| `dextra reply <thread-id> "text"` | reply to a comment | 50 |
| `dextra comments <video>` | read the comments of a video | 1 per page |
| `dextra subs` | list your subscriptions | 1 per page |
| `dextra sub <channel>`, `unsub <channel>` | subscribe or unsubscribe (`@handle`, `UC…` id or link) | 50 + 1–2 |
| `dextra playlists` | list your playlists | 1 per page |
| `dextra pl-new "title" [--privacy private]` | create a playlist | 50 |
| `dextra pl-add <playlist-id> <video>` | add a video to a playlist | 50 + 1 |
| `dextra pl-items <playlist-id>` | list the videos of a playlist | 1 per page |
| `dextra liked` | list your liked videos | 1 per page |
| `dextra quota` | today's quota use, by Dextra's own count | — |
| `dextra log` | the local log of actions taken on the account | — |
| `dextra revoke` | revoke access at Google and delete the local token | — |

A video can be given as an id or as any YouTube link (`watch`, `youtu.be`, `shorts`, `live`).

Watch Later and watch history cannot be managed this way: the YouTube Data API has not
exposed them since 2016.

## Setup

Python 3.9 or newer; standard library only.

1. In the Google Cloud console, create a project and enable **YouTube Data API v3**.
2. In **Google Auth Platform**, configure the consent screen (user type External) and add
   the scope `https://www.googleapis.com/auth/youtube.force-ssl` under **Data Access**.
3. Under **Clients**, create an OAuth client of type **Desktop app** and download its JSON.
4. Save it as `~/.config/dextra/client_secret.json`, put `dextra` on your `PATH`, and run
   `dextra auth`.

Google shows an "unverified app" screen during sign-in: the app is your own and has not
been submitted for verification. While the app is in the **Testing** publishing status,
Google ends the sign-in after 7 days; publishing it to **In production** removes that limit.

## Quota

Every Google Cloud project gets 10,000 units a day. A read costs 1 unit; a write (rating,
comment, subscription, playlist change) costs 50, so roughly 200 actions a day. The quota
resets at midnight Pacific Time. Dextra keeps its own count in
`~/.local/state/dextra/quota.json`.

## Privacy

See [PRIVACY.md](PRIVACY.md). In short: tokens and logs stay on your computer with
owner-only permissions, and Dextra talks only to Google.

## Authors

Made by Aiken and Claude.
