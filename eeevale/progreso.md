# Course Planner — Roadmap / Known Issues

Snapshot from a code review of the current backend (`FastAPI` + `psycopg2`) and frontend (`React` + `ReactFlow`). Organized by priority so you have a clear path forward.

---

## 2. Backend Bugs

### `getProyeccion` drops leftover skipped courses

After the main loop over `courses` finishes, anything still sitting in `skippedCourses` is never flushed into a semester. If the course list ends without one more credit-limit overflow to trigger reprocessing, those courses silently disappear from the projection instead of being scheduled.

**Fix direction:** after the main loop, keep generating semesters from `skippedCourses` (looping until it's empty or no more courses can be unlocked) instead of relying on the loop to end with everything resolved.

### `getCourses` query has no `ORDER BY`

The projection algorithm assumes `courses` is sorted by semester (used both to find the student's "current semester" and in the main scheduling loop), but the SQL query never sorts by `semester`. It likely works today by accident (insertion order), but it's fragile.

**Fix direction:** add `ORDER BY semester` (and probably `code`, for stable tie-breaking) to the query in `connection.py`.

### Hardcoded course skip

`if course['code'] == 'ECIN-08606': continue` is a one-off hack skipping a specific course (looks like Práctica/Titulación) instead of a general rule.

**Fix direction:** decide on a real rule for "non-schedulable" courses (e.g. a DB flag like `is_special` or `excluded_from_projection`) instead of a hardcoded code.

---

## 3. Frontend Bugs

### Reset-progress button sets wrong type

In `BotBar.jsx`: `setProgress((prev) => "")` sets progress to an empty **string** instead of an empty **object** (`{}`). Works by accident currently, but it's a type inconsistency that could break if other code starts relying on `progress` always being an object (e.g. `Object.keys(progress)`).

### "Enviar" button is a stub

The progress-submit button in `BotBar.jsx` has no `onClick` — it currently does nothing.

### Missing CSS variable

`--course-border` is referenced in `CourseNextNode.jsx` (for the `Handle` background color) but never defined in either theme block in `index.css`. The connection-point handles are rendering with an invalid/undefined color.

### `CareerSelector` has no loading/error state

If the `/courses` fetch fails or is slow, nothing visible happens — only a `console.error`. The user just sees an unresponsive button.

---

## 4. Dead Code / Cleanup

- **`backend/proyection.py`** — looks like an old scratch/test version of the projection algorithm, with hardcoded sample data and a bare `print()` that runs on import. Safe to delete or move into an actual test file.
- **`src/components/CourseNode.jsx`** — appears superseded by `CourseNextNode.jsx` but is still in the repo, unused. It had more functionality than the current node (4 status states: Aprobado/Reprobado/Inscrito/Bloqueado, plus a `colorMode` toggle for difficulty-based coloring) — worth deciding if that should be ported over or if it's intentionally retired.
- **`src/components/CourseMain.jsx`** — unused. Looks like an intended course-detail panel that was never wired up to `selectedCourse` in `CurriculumGraph.jsx`.

---

## 5. Infrastructure / Polish

- **CORS misconfiguration:** `main.py` sets `allow_origins=["*"]` together with `allow_credentials=True`. Browsers reject that combination for credentialed requests — fine for now since nothing uses cookies/auth, but will silently break if that changes.
- **No cache invalidation:** the in-memory `cache` dict in `connection.py` never expires or refreshes, so DB changes won't show up until the server restarts.
- **No backend persistence of progress:** progress is stored only in `localStorage`, so it doesn't sync across devices. May be intentional for now, but worth a decision either way.

---

## Suggested Order

1. Fix the `getProyeccion` dropped-courses bug (correctness first — no point building UI on top of wrong data).
2. Add `ORDER BY semester` to `getCourses`.
3. Build the projection UI and wire it to `/proyection`.
4. Fix the small frontend bugs (`setProgress("")`, missing `--course-border`, stub button).
5. Clean up dead files (`proyection.py`, decide fate of `CourseNode.jsx` / `CourseMain.jsx`).
6. Infrastructure polish (CORS, cache invalidation, progress persistence) once the core flow is solid.