# Minors / Electives Feature — TODO

## Data / Backend

- [x] Load ITI course data (`MNOR-40001`-style codes) into `courses`, following the same pattern as ICCI's `insert_minors.py`
- [x] Link ITI courses into `minor_courses`, making sure `minor_id` lookups filter by `career = 'ITI'` (not the ICCI row with the same name)
- [x] Chain ITI's prereqs (1→2→3→4) the same way as ICCI's, scoped to `career = 'ITI'`
- [x] Load ICI course data + minor links + prereq chains (same full pipeline — not started yet)
- [x] Confirm ICI's actual `start_semester` (currently defaulted to 5 in the migration — double-check this is correct rather than assumed)
- [x] Add each minor's first-course external prereq manually (per minor, as planned)
- [x] Update `getMinors` (Python/backend) to filter by `career` column instead of the old array — only the Supabase frontend version got fixed so far
- [x] Add `ORDER BY semester` to `getCourses()`'s SQL query if not already present, since `getProyeccion()`'s in-order logic depends on it

## Frontend

- [x] Fix hardcoded `const minorId = 1` in `handleSendProgress` → use `selectedMinorId` instead
- [x] Update `applyMinorToCourses` to match by `UNFP-` prefix + semester (career-agnostic), not the old hardcoded semester assumption
- [x] Clean up dead code (`const result = new Set()` in `highlightedIds`)
- [ ] On returing from `getProyeccion()`, the minor does not get reloaded.
- [ ] Decide GitHub Pages routing strategy (`HashRouter` vs. `BrowserRouter` + 404 redirect trick) before the projection graph route goes live, so refresh/direct links don't 404

## Open design questions to resolve

- [ ] Confirm whether `minor_courses` position→semester logic needs anything beyond `start_semester + position - 1` for any future minor shapes
- [ ] Decide whether minor selection should live in a form (submit-based) or trigger re-projection immediately on change