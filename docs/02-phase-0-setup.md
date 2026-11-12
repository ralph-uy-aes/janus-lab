# Phase 0: Decisions and Setup

**Status:** Complete

## The Goal
Before any hardware is plugged in, the foundation of the lab must be built. Phase 0 was about making decisions, setting up the documentation infrastructure, and establishing a secure workflow. 

## The Documentation Split
A security project requires two layers of documentation:
1.  **The Private Vault:** Holds everything—IP addresses, serial numbers, budget figures, raw command outputs, and mistakes.
2.  **The Public Repo (this one):** Holds sanitized write-ups, diagrams, and lessons learned.

To enforce this split, I set up a private Obsidian vault and this public GitHub repository. To prevent accidental secrets from leaking into this public repo, I installed `gitleaks` as a pre-commit hook. (Tested successfully: a fake AWS key was blocked).

## The Infrastructure Decisions
Several major architectural decisions were made and documented in Decision Records (DRs):
*   **Budget:** A strict ceiling was set for the entire build to prevent scope creep.
*   **Security:** A password manager was configured with MFA and a physical offline recovery kit was assembled.
*   **The Topology Pivot:** The original plan was to move the ISP modem into the lab room. This was abandoned due to the risk of disturbing household internet and coax wiring. Instead, a dedicated Lab Router was purchased to act as the primary gateway, with an enterprise firewall sitting behind it to enforce zone isolation.

## The Purchasing & Inventory
*   All hardware for Phase 1 was ordered or sourced (including a donated UPS and a label maker).
*   Every hard drive on hand was physically labeled with a unique ID (e.g., `ATL-SSD-1`, `BRK-SSD-1`) and logged in the private inventory to track health and assignment.

## Lessons Learned
*   **`sudo` is dangerous for user-space tools.** The `gitleaks` installation on macOS failed twice due to root-owned cache files left behind by a previous `sudo` command. The fix was to reclaim ownership of the cache directories and never run pre-commit hooks with elevated privileges.
*   **Verify your staging area.** The initial `gitleaks` test on Windows falsely passed because the test file wasn't actually staged in git. A block test that doesn't verify `git status` proves nothing.