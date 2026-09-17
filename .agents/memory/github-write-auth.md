---
name: GitHub write authentication
description: GitHub token behavior encountered when publishing this workspace
---

For GitHub publishing, verify an actual write operation rather than relying only on repository metadata or read access. A token can list repositories and report repository permissions while Git HTTPS pushes and Git Data API writes still return 403 until the token has explicit repository Contents write access.

**Why:** This workspace encountered successful account/repository reads followed by 403 responses for both Git push and Git Data API writes.

**How to apply:** Use a fine-grained token scoped to the destination repository with Contents set to Read and write, or a classic token with the `repo` scope. Keep the token in the workspace secret flow and never place it in chat or command output.