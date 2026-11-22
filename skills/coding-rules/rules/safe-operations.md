# Safe operations
- Verify paths and file contents before editing; never guess structure.
- If the user says they reverted something, trust it; don't re-revert with git.
- Local infrastructure (e.g. `docker compose` services) may be started or stopped when the task needs it; say what you start. Never touch remote or shared environments (deployments, release pipelines) without confirmation.
