# Good first issues

Seeded issues for new contributors. File each one on GitHub with
the `good first issue` and `help wanted` labels.

## 1. Add a reply queue table

Title: Show the reviews that need a reply first, top-down

Description: After the per-product summary, print a short table
of the unreplied negative reviews sorted oldest first
(review id, product, rating, days waiting), so a store
owner can work the reply queue top-down without reading
every finding. Overdue reviews come first, then the rest
in date order. Reviews with no date go last.

Difficulty: Easy

Acceptance criteria: the table appears in text output with
the correct order for the sample file (R-106 and R-107
first, both 12.6 days waiting, then R-102, R-110, R-105,
and the two R-101 rows); JSON output is unchanged; a test
checks the table rows.

## 2. Add a configurable author burst threshold

Title: Let the fake-review author burst count be configurable

Description: Add a --fake-author-count flag that sets how
many reviews from one email count as an author burst. The
default stays at four.

Difficulty: Easy

Acceptance criteria: an author with three reviews is
flagged as a burst when --fake-author-count 3 is passed,
and is not flagged without the flag; a test covers both
cases; README documents the flag.

## 3. Report the worst rated product in the summary

Title: Print the lowest rated product with enough reviews

Description: Add one line to the text summary naming the
product with the lowest average rating among products with
at least --min-reviews reviews (product id, name, average
rating, review count), so a store owner can see the
biggest product problem at a glance. When no product
reaches the minimum, the line is omitted.

Difficulty: Easy

Acceptance criteria: the line appears for a file where a
product has five reviews averaging 1.00; it is absent for
the sample file, where no product reaches five reviews;
JSON output is unchanged; a test checks both cases.

## 4. Flag verified versus unverified negative reviews

Title: Split unreplied negatives by verified purchase

Description: Add the verified purchase split to the
per-product summary lines: the unreplied negative count
followed by how many of them are from verified owners,
for example "unreplied negatives: 3 (2 verified)". The
verified_owner column already parses, so no input change
is needed. Reviews with an empty verified value count as
unverified.

Difficulty: Easy

Acceptance criteria: the sample file shows P-201 with 3
unreplied negatives (3 verified) and P-203 with 3
unreplied negatives (0 verified); JSON per-product rows
gain a verified_unreplied_negatives field with the same
numbers; a test checks both.
