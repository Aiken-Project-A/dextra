# Dextra Privacy Policy

Effective date: 21 October 2026

Dextra is an open-source command-line tool that runs entirely on the user's own computer.
It is used by the owner of this repository with their own Google account. It has no
server, no backend, no analytics and no telemetry. This policy explains what Dextra does
with data from Google.

## Data Dextra accesses

With the user's permission, granted on Google's OAuth consent screen (scope
`https://www.googleapis.com/auth/youtube.force-ssl`), Dextra calls the YouTube Data API on
the user's behalf, and only when the user runs a command. Depending on the command, it
reads or changes:

- basic information about the user's channel;
- the user's ratings of videos (likes and dislikes);
- comments the user posts, and public comments on videos the user asks to read;
- the user's subscriptions;
- the user's playlists and their items.

## How data is used

Data is used only to carry out the command the user typed and to show the result in the
user's terminal. Dextra does not use it for advertising, profiling or any other purpose.

## Storage

Dextra stores the following on the user's computer, readable only by the user:

- the OAuth tokens (`~/.config/dextra/token.json`);
- a log of actions taken on the account: time, action, video or channel id, and the title
  or comment text (`~/.local/state/dextra/actions.log`);
- a daily count of API quota use (`~/.local/state/dextra/quota.json`).

Nothing is stored anywhere else.

## Sharing

Dextra does not sell, share or transfer user data to anyone. Data travels only between
the user's computer and Google's servers (`accounts.google.com`, `oauth2.googleapis.com`,
`www.googleapis.com`).

Dextra's use and transfer of information received from Google APIs adheres to the
[Google API Services User Data Policy](https://developers.google.com/terms/api-services-user-data-policy),
including the Limited Use requirements.

## YouTube API Services

Dextra uses YouTube API Services. By using Dextra you agree to the
[YouTube Terms of Service](https://www.youtube.com/t/terms). How Google handles your data
is described in the [Google Privacy Policy](https://policies.google.com/privacy).

## Revoking access and deleting data

- Run `dextra revoke` to revoke access at Google and delete the local token.
- Or remove Dextra's access in your Google Account security settings:
  <https://security.google.com/settings/security/permissions>.
- Delete `~/.config/dextra` and `~/.local/state/dextra` to remove all local data.

## Children

Dextra is not directed at children.

## Changes

Changes to this policy are made in this file; their history is in this repository's git
log.

## Contact

Open an issue at <https://github.com/Aiken-Project-A/dextra/issues>.
