# Keeping It Kayfabe Pick'em

Season-long prediction sheet for WWE premium live events, for the Keeping It Kayfabe watch-alongs. Hosted on GitHub Pages, with picks stored in Firebase Firestore so everyone with the link sees the same scoreboard live.

## Files

- `index.html` is the whole site: the match cards, scoring, season standings and the Firebase connection.
- `firestore.rules` holds the database security rules. Paste them into Firebase console → Firestore Database → Rules → Publish.

## Adding the next event

Add an entry to the `EVENTS` array in `index.html` with its matches and props. Ladder matches are worth 3 points, Last Man Standing 2, everything else 1. Event ids must be lowercase letters and digits.

## Data layout (Firestore)

- `events/<eventId>`: `{ results: { matchId: winningOptionIndex } }`
- `picks/<eventId>-<host>`: `{ sel: { matchId: pickedOptionIndex } }` (host 0, 1 or 2, in the order shown on the scoreboard)
- `season/settings`: `{ names: [host1, host2, host3] }`
