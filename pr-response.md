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
Created a new file tests/test_watchlist.py and added a test  called test_add_to_watchlist_nonexistent_film_raises.

This follows the same testing scheme as test_collection.py. I used the same pytest.fixtue of app, sample_user, and sample_film to create an environment for the test to run.  
**How I verified:**
Ran the new test and ensured it passed, and ran the entire testing suite using pytest to ensure nothing conflicted.
## Comment 4 — Default visibility
**My position:**
The system should have watchlists as visible by default. This increases user engagement and ease of sharing watchlists.
**Reasoning:**
Having watchlists be defauly visible is useful as it allows users to more easily find and share lists with other people. It allows users to share with their friends after creation withou an additional step, and allows other users to find what movies people are adding to their watchlist. This makes the website more social, increasing engagement with the site.

**Tradeoff acknowledged:**
The tradeoff is users now must have an extra step to hide their watchlists, and may not want to use a site that does so. It also reduces user privacy as users may expect the lists to be private by default. However, the user engagement increase and ease of sharing make the tradeoff worht it.
## Comment 5 — Sort order
**My position:**
Sort order should be alpahbetical by default. This makes it easier to find films by title.
**Reasoning:**
Sorting alphabetically makes it easier to find films by title, rather than having users scroll through a potentially long list.
**Engagement with reviewer's point:**
While users may want to see what they added recently, they also want to find things they added before. Users may not remember when they added a film, but will remember the name, making it easier to find and watch.
## Comment 6 — Rebase
**What conflicted:**
.gitignore conflicted in both files. The 
**How I resolved it:**
**How I verified no conflict remains:**

## PR Description
<!-- Written at the end — feature overview, design decisions, manual testing steps -->