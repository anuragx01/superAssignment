# Notes

## Summary of changes

I corrected task search so archived tasks remain excluded and status filters apply to both title and description matches. I aligned the H2 query and Oracle reference, escaped LIKE wildcards, and moved pagination into the database with bounded page sizes and clear 400 responses for invalid inputs. In the frontend, I added debouncing and cancellation for stale searches, error recovery, and page resets when filters change. I also removed the artificial backend delay and raw query logging, added accessible filter labels and horizontal table scrolling, and made the Vite API target configurable.

## What I chose not to change

I did not add authentication because the app has no user or identity model; introducing one would change its architecture and local workflow. I kept the H2 console available for documented local development.

## Biggest remaining risk

The API has no authentication. If exposed outside a trusted development environment, callers could read task data; deployment needs an access-control boundary.

## Tools and AI

I used Codex to assist with code inspection and implementation, then reviewed the diff and the query and request-state changes. Maven compilation and the Vite production build succeeded; I did not run automated tests. The running backend still returned the old, unfiltered results during my API check, so it must be restarted before verifying the updated filter at runtime.
