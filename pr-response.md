# PR Response Doc — CineLog Watchlist Feature

## AI Usage
<!-- Fill in at the end — how you used AI tools during this project -->

## Comment 1 — Rename
**What I did:**
Renamed save_to_watchlist() to add_to_watchlist() in services/watchlist_service.py and changed all instances.
**How I verified:**
Used VS Code global search to change it. I also checked the references to the function to ensure none were missed.

## Comment 2 — Deduplication
**What I did:**
Added deduplication logic to add_to_watchlist() in services/watchlist_service.py following the pattern in add_to_collection fromn services/collection_service.py. I also created an Class AlreadyInWatchlistError to take the Exception
**How I verified:**
Checked watchlist_service and collection_service, ensuring they had the same patter and changing CollectionEntry to WatchlistEntry in watchlist_service. I also ran a current pytest to ensure nothing broke.
## Comment 3 — Missing test
**What I did:**
**How I verified:**

## Comment 4 — Default visibility
**My position:**
**Reasoning:**
**Tradeoff acknowledged:**

## Comment 5 — Sort order
**My position:**
**Reasoning:**
**Engagement with reviewer's point:**

## Comment 6 — Rebase
**What conflicted:**
**How I resolved it:**
**How I verified no conflict remains:**

## PR Description
<!-- Written at the end — feature overview, design decisions, manual testing steps -->