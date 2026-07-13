# PR Response Doc — CineLog Watchlist Feature

## AI Usage

## Comment 1 — Rename
**What I did:**
I renamed save_to_watchlist to add_to_watchlist using the "rename symbol" feature in VS Code 
**How I verified:**
After the changes, I ran the flask api and tested the endpoint to ensure that it still worked as expected.

## Comment 2 — Deduplication
**What I did:**
I added logic to check if a film is already in the watchlist before adding it.
**How I verified:**
I wrote a test case that attempts to add the same film twice to the watchlist and verified that it raises an AlreadyInWatchlistError.

## Comment 3 — Missing test
**What I did:**
Added the test for a adding an invalid film to the watchlist 
**How I verified:**
Ran the test and confirmed that it raises a FilmNotFoundError when trying to add a film that does not exist in the database.

## Comment 4 — Default visibility
**My position:**
I feel like we should keep the default visibility of the watchlist to public
**Reasoning:**
This is because the watchlist is meant to be a social feature, and this application is supposed to be a public sharing platform, so users likely want to share what they have watched with others. 
**Tradeoff acknowledged:**
Some users might not want their watched movies to be public, and there will be extra steps for those users to change the visibility to private.

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