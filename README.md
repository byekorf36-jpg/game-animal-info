# Game Animal Records — Shared Farm Edition

A mobile-friendly animal-records app for game animals, bulls and rams. Each animal has its own named profile, identity/genetics fields, auction details, dated measurement history and photos.

## Shared access
- Farm owner creates a workspace and shares its Farm ID + invitation code.
- Invited users join with their own email/password account.
- **All invited users have editor access**: they can view, add, edit and delete animal records.
- The owner controls the farm workspace and invitation code.

## Before real use
This is a development project, not yet a published or production-certified app. Create your own Firebase project, enable Email/Password Authentication, Firestore and Storage, add the Firebase web configuration to `www/index.html`, and deploy `firestore.rules` and `storage.rules`. Test with two separate accounts and phones before entering important livestock records. Keep regular JSON backups.

See `FIREBASE_SETUP.md` for setup instructions. Android build output (`.aab`) and Play Store publication are separate remaining steps.
