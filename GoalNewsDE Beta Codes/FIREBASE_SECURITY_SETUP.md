# GoalNews Firebase security setup (no backend)

## Firestore

1. Open Firebase Console → **Firestore Database** → **Rules**.
2. Replace the entire current ruleset with the contents of `firestore.rules`.
3. Confirm the two trusted admin UIDs in `isAdmin()` match the intended accounts.
4. Publish the rules. Do not keep the old wildcard `match /{document=**}` rule: Firestore combines matching `allow` statements with OR, so a broad rule would still grant access.

The rules restrict user documents to their owner and admins, keep user emails private, and disallow browser writes to coins and reward fields. Comments and ratings are validated. The old client-side poll totals are read-only; match tips remain one vote per signed-in account and match.

## Firebase Storage

If GoalNews profile avatars use Firebase Storage, open Firebase Console → **Storage** → **Rules**, replace the existing rules with `storage.rules`, and publish. Avatar files are publicly readable, but only the signed-in owner can upload or replace a PNG/JPEG under their own UID. Uploads are limited to under 5 MB.

## Features paused for security

- Daily Spin, Coin-Shop purchases, admin coin changes, and Advent calendar rewards.
- Client-side voting totals on the legacy polls.
- Comment reactions, because the current client can set arbitrary reaction totals.
- The old visit logger; it no longer records browser visits.

Existing coin balances and already-owned profile extras remain stored and visible, but browser clients cannot change them.

## Important

These files are local drafts. They do not change Firebase until the rules are published in the Console. The rules do not provide rate limiting for authenticated form submissions; a backend or additional abuse protection would be needed for that.
