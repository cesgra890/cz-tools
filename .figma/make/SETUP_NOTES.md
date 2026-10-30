# Initial import setup notes

## Deployment verification blocker

Bootstrap and deploy-preview verification succeed. The deployment script builds
the same static artifact shape, including the required root `index.html`, but
`figma make verify-deploy` exits with status 1 immediately after reporting that
it hashed five files. The verifier provides no current stderr or more specific
error.

Attempted repairs:

- Added the required generated root index to replace Apache directory indexing.
- Removed `.htaccess` from the static artifact because it is not used by the
  static adapter.
- Confirmed temporary artifact cleanup is not causing the failure.
- Passed the `static` adapter explicitly.

Last verifier output: `.figma/make/deploy: exit status 1` after `Hashed 5 files`.
The deployment verifier or its one-time validation handoff needs investigation;
no application or credential changes are indicated by the available diagnostic.
