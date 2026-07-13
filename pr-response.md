# PR Response Doc — CineLog Watchlist Feature

## AI Usage
Comment 4 and 5- I used ChatGPT to run through my arguements and make sure I hadnt missed any tradeoffs. I had overlooked a privacy concern and was able to address it more directly.

Comment 6- During the rebase I wasn't sure how to merge or what I was looking to resolve. I used ChatGPT to ask about the rebase process and what I had to do to make merge the branches successfully. Based on this, I was able to accept the changes and continue with commit process.


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
.gitignore conflicted in both files. This was resolved, then I was able to rebase

However, after doing so tests failed as WatchListEntry in models no longer existed. I checked feature breanch and took the model and added it back to the models.
I had to ask ChatGPT how to resolve the conflicts present in multiple files. my tests were deleted as were changes I had made in the feature branch before rebasing with main.
**How I resolved it:**
Used git log --oneline origin/main..HEAD to get all commits, and went through conflicts one at a time using VS Code built in merge editor. This took longer than fixing the bugs.
**How I verified no conflict remains:**
I re ran the application an ensured the tests passed. I also checked my changes and used git rebase --continue which ran without errors.
## PR Description
The new watchlist feature allows users to add films to their watchlist, which is publically visible by default. Sort order is alphabetical to allow users to more easily find films in their list by name.

Manual tests were done by using pytest and Postman, an API testing application. I added films to a user watchlist and ensured it worked as intended.
## Stretch Goals

### remove_from_watchlist()
Added remove_from_watchlist in watchlist_service file, allowing users to remove an item from their watchlist.

### Second test

Added test for test_add_to_watchlist_creates_entry and test_remove_to_watchlist_creates_entry.

These tests check for watchlist item creation and removal. Confirmed working

### Public toggle
Added a public to watchlist.py under routes to take a public parameter. This parameter is set to default True if not supplied. It is then fed to the add_to_watchlist function under watchlist_services.py.


Commit history:
5f23236 feat: added watchlist model and endpoint fixed a bug more changes
9f86c62 Comment 6 Rebase- resolve failing tests by adding Watchlistentry class to main, and update to use UUID
7f6a9fd docs: comment 4 and 5 addressed, no updates to code made.
b22ccbc fix: Comment 3 missing test for test_watchlist added, test test_add_to_watchlist_nonexistent_film_raises created and verified working with current test suite
2f1e2f2 fix: Comment 2 Deduolication logic added to add_to_watchlist from add_to_collection pattern
261c0ed fix: Comment 1: Renamed save_to_watchlist to add_to_watchlist to conform with the coding styles. Updated files watchlist_service and routes/watchlist/watchlist.py
9f24b7d fix: Comment 6 Step 1 Rebase with .gitignore change to update feature to main
a3aa00c fix: update film retrieval method to use db.session.get in collection and watchlist services
a5b9a76 feat: added watchlist model and endpoint fixed a bug more changes
f8de9fb AI usage
9d45f53 Merge branch 'feature/watchlist' of https://github.com/bmurdata/ai201-project6-cinelog-starter into feature/watchlist
9cada4c Comment 6 Rebase- resolve failing tests by adding Watchlistentry class to main, and update to use UUID
3d986ab Update: comment 4 and 5 addressed, no updates to code made.
5ac493a fix: Comment 3 missing test for test_watchlist added, test test_add_to_watchlist_nonexistent_film_raises created and verified working with current test suite
45f5386 fix: Comment 2 Deduolication logic added to add_to_watchlist from add_to_collection pattern
cd83b3d Comment 1: Renamed save_to_watchlist to add_to_watchlist to conform with the coding styles. Updated files watchlist_service and routes/watchlist/watchlist.py
7a8a19e Comment 6 Step 1 Rebase with .gitignore change
326edc2 fix: update film retrieval method to use db.session.get in collection and watchlist services
478e73f added watchlist model and endpoint fixed a bug more changes
159fd66 Update: comment 4 and 5 addressed, no updates to code made.
5c3468f fix: Comment 3 missing test for test_watchlist added, test test_add_to_watchlist_nonexistent_film_raises created and verified working with current test suite
9df783e fix: Comment 2 Deduolication logic added to add_to_watchlist from add_to_collection pattern
16c2685 Comment 1: Renamed save_to_watchlist to add_to_watchlist to conform with the coding styles. Updated files watchlist_service and routes/watchlist/watchlist.py
bbe206c (origin/main, origin/HEAD, main) Merge pull request #2 from ascherj/chore/add-gitignore
718a9a8 chore: add .gitignore for generated files
7c37bcd fix: update film retrieval method to use db.session.get in collection and watchlist services
ec90edb added watchlist model and endpoint fixed a bug more changes
07ca580 refactor: migrate film IDs from integer to UUID
014ae54 feat: initial CineLog API with film collection feature