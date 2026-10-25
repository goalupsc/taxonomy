# goalupsc taxonomy: data release

This release contains a 187-tag taxonomy derived from the UPSC Civil Services syllabus (Examination Notice No. 05/2026-CSE), and its links to past examination questions and to textbook passages. Tags were assigned by language models (Claude Sonnet 5 for 2013-2026; Claude Haiku 5.5 for Prelims 1993-2012) from a closed list of tags, with automated validation of the output.

Questions are identified by year and question number so that they can be located in the official papers. **No question text, options, answers, explanations or textbook text is included.** Textbook links are given as per-tag counts only; chunk-level links are withheld because chunk boundaries do not reliably follow chapters or pages.

## Counts

- Taxonomy tags: 187 (GS I 36, GS II 49, GS III 44, GS IV 37, Prelims Paper I 21).
- Prelims questions with at least one taxonomy tag: 4188 (1993-2026); Mains GS1-4 questions with at least one taxonomy tag: 1041 (2013-2026).
- Question-tag links (taxonomy tags): Prelims 14695, Mains 3569.
- Taxonomy tags linked to at least one textbook passage: 135.
- Annotated spot-check pairs: 271.

## Files

All files are UTF-8, comma-separated, with a header row.

- `taxonomy.csv` - one row per taxonomy tag. `tag_id`; `name` (full tag name, `Examination-Topic[-Subtopic]`); `paper` (GS I, GS II, GS III, GS IV, Prelims Paper I); `topic`; `subtopic` (blank if none); `level` (2 = paper and topic, 3 = paper, topic and subtopic); `parent_tag_id` (blank for every row: the taxonomy has no tag that is the parent of another); `is_remainder` (true for the two residual "REMAINDER" subtopics).
- `paper_two_tags.csv` - the five Prelims Paper Two tags (same columns plus `note`). They mark aptitude items in the pre-2011 single Prelims paper and are not part of the taxonomy.
- `question_tags.csv` - one row per question-tag link, for taxonomy tags and Paper Two tags. `corpus` (prelims/mains); `question_id` (identifier internal to this release); `year`; `paper` (Prelims Paper I, or GS1-GS4 for Mains); `question_number` (number within that year's paper; for Mains it is a label such as `GS1-2013-1`); `tag_id`; `confidence` (0-100, as reported by the model); `tagging_period` (1993-2012 or 2013-2026). Mains Essay questions are omitted.
- `per_tag_summary.csv` - per taxonomy tag: `n_prelims_questions`, `n_mains_questions`, `n_chunks` (number of textbook passages linked to the tag), `has_question`, `has_chunk`.
- `spot_check.csv` - 271 manually annotated question-tag pairs: `sample` (2013-2026 or 1993-2012), `corpus`, `question_id`, `year`, `question_number`, `tag_id`, `confidence`, `correct` (y/n; one pair is unannotated and left blank).
- `validation.md` - checks recomputed from these files.

LICENSE: TBD
