# PR Response Doc — CineLog Watchlist Feature
Logs are shown in ``logs.png``


## AI Usage
I used VS Codes Autocomplete feature to help rewrite some code in watchlist_service.py as well as helping me to write some of the text in this document.

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
I am okay with your suggestion to sort the watchlist by date added instead of title.
**Reasoning:**
This makes sense because users might want to see the most recently added films first, and it is more intuitive to sort by date added for a watchlist feature.
**Engagement with reviewer's point:**
I agree with your reasoning that most users want to see what they added recently, so I think its good to keep the sorting like this from now on. 


## Comment 6 — Rebase
**What conflicted:**
The .gitignore file and models.py were conflicting with each other
**How I resolved it:**
I kept my changes on the gitignore, since my new gitignore includes all of the ignored files from the previous gitignore
I added the functions from my new branch into models.py whilst keeping the refactored functions from the main branch, so that the models.py file has the models for the watchlist as well as the refactored film model functions.
**How I verified no conflict remains:**
I ran the API and tests to see if they were working, and I also checked the history of the files to ensure that the changes were merged correctly and that there were no remaining conflicts.

## PR Description
<!-- Written at the end — feature overview, design decisions, manual testing steps -->
**Added Watchlist Feature**

This watchlist keeps track of all of the films that a user has added to their watchlist. 
The watchlist is public by default, but users can change the visibility to private if they wish. 
The watchlist is sorted by date added, with the most recently added films appearing first.

To test the features, run ``pytest`` to automatically run all of the tests

#### The open endpoints for the watchlist feature are as follows:
``/watchlist/<user_id>`` - GET - returns the watchlist for the user with the given user_id
``/watchlist/<user_id>/add`` - POST - adds a film to the watchlist for the user with the given user_id

Manually test the endpoints by running the flask api and using a tool like Curl to send requests to the endpoints.