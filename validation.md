# Validation

## a. Row counts (data rows, excluding header)

| File | Rows |
|---|---|
| taxonomy.csv | 187 |
| paper_two_tags.csv | 5 |
| question_tags.csv | 18541 |
| per_tag_summary.csv | 187 |
| spot_check.csv | 271 |

## b. Recomputed from the release files alone vs paper_numbers_5

Checks that needed chunk-level rows (chunk-tag links 5685; chunks with zero taxonomy tags 450) were dropped with the chunk files.

| Check | Recomputed | Expected | Result |
|---|---|---|---|
| taxonomy tags | 187 | 187 | OK |
| per paper | [36, 49, 44, 37, 21] | [36, 49, 44, 37, 21] | OK |
| Table II: tags with >=1 question, per paper (question_tags.csv) | [36, 49, 44, 37, 21] | [36, 49, 44, 37, 21] | OK |
| Table II: tags with >=1 question, total | 187 | 187 | OK |
| Table II: tags with >=1 chunk, per paper (per_tag_summary.csv) | [35, 40, 33, 7, 20] | [35, 40, 33, 7, 20] | OK |
| Table II: tags with >=1 chunk, total | 135 | 135 | OK |
| Table II: tags with both | 135 | 135 | OK |
| has_chunk agrees with n_chunks>0 for all tags | True | True | OK |
| per_tag_summary question counts agree with question_tags.csv | True | True | OK |
| Prelims questions with >=1 taxonomy tag | 4188 | 4188 | OK |
| Mains questions with >=1 taxonomy tag | 1041 | 1041 | OK |
| total | 5229 | 5229 | OK |
| questions sharing >=1 tag with >=1 chunk (via has_chunk) | 4748 | 4748 | OK |
| ... as % (rounded) | 91 | 91 | OK |
| Prelims question-tag links (taxonomy) | 14695 | 14695 | OK |
| Mains question-tag links | 3569 | 3569 | OK |
| Prelims questions carrying only Paper Two tags | 111 | 111 | OK |
| Paper Two tagged questions that also have a taxonomy tag | 0 | 0 | OK |
| spot check 2013-2026: y / total | 158/208 | 158/208 | OK |
| spot check 1993-2012: y (blank counted y) / total | 49/63 | 49/63 | OK |
| spot check combined pairs | 271 | 271 | OK |

Mismatches: 0

Spot-check rows with blank `correct`: 1 (question_id 3966, tag_id 186)

## Data notes

- `parent_tag_id` is blank for all 187 rows: the database stores no parent relation, and no level-3 tag has a matching level-2 tag.
- Topic and subtopic come from the database relations and match the hyphen split of `name` for all 192 tags. No topic or subtopic name contains a hyphen.
- No syllabus source sentence is stored in the database, so that column is omitted.
- Mains `question_number` is a label (e.g. `GS1-2013-1`), not an integer.
- Mains questions span years 2013-2026; tagging_period is 2013-2026 for all of them.

## d. Header rows

- `paper_two_tags.csv`: `tag_id,name,paper,topic,subtopic,level,parent_tag_id,is_remainder,note`
- `per_tag_summary.csv`: `tag_id,name,paper,n_prelims_questions,n_mains_questions,n_chunks,has_question,has_chunk`
- `question_tags.csv`: `corpus,question_id,year,paper,question_number,tag_id,confidence,tagging_period`
- `spot_check.csv`: `sample,corpus,question_id,year,question_number,tag_id,confidence,correct`
- `taxonomy.csv`: `tag_id,name,paper,topic,subtopic,level,parent_tag_id,is_remainder`

No column holds question text, options, answers, explanations, statements or chunk text, and no chunk-level file remains.

## c. Anonymity scan

Scanned all 7 files (the `.git` directory is not scanned here; see the transcript note) (case-insensitive substring) for 35 terms (author surnames, institution and city, email provider, email and URL markers, path fragments, host name, database name, OS username, and every username/email/first/last name in the user table; the term list is deliberately not reproduced in this file). Total hits: 1; of which the expected product-name hit in README.md: 1; unexpected hits: 0.

- README.md line 1: term #17

## e. Folder listing

| File | Bytes |
|---|---|
| paper_two_tags.csv | 928 |
| per_tag_summary.csv | 19495 |
| question_tags.csv | 934075 |
| README.md | 2770 |
| spot_check.csv | 10444 |
| taxonomy.csv | 28245 |
| validation.md | 3882 |
