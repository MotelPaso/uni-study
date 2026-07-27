# Feature Ideas

## For Students

- [ ] **Credit counter / progress bar** — show total credits completed vs. required for graduation. Currently you only see individual course statuses but no overall progress metric.
- [ ] **Semester GPA estimator** — let students input expected grades per course and show a running GPA estimate. Useful for planning which semesters to load up.
- [ ] **Export/share plan** — export the curriculum graph or projection as a PNG/PDF. Students often need to share their plan with advisors.
- [ ] **Undo/redo in edit mode** — one wrong click cycles through all statuses. A history stack (Ctrl+Z) would save a lot of frustration.
- [ ] **Course search/filter** — when the graph is big, clicking through it to find a specific course is slow. A search bar that highlights and zooms to a course would help.
- [ ] **Conflict detection** — warn if a student marks courses as "ongoing" that have unmet prerequisites, or if they exceed a credit limit in a semester.
- [ ] **Multiple plan versions** — let students save different scenarios (e.g., "take minor" vs. "no minor") and switch between them, instead of overwriting the single localStorage plan.

## Backend / Data

- [ ] **Course descriptions / syllabus links** — the graph shows code and title, but students often need to know what a course actually covers. Add a detail panel when clicking a course.
- [ ] **Historical approval rates as a visual indicator** — you already fetch `approvalrate` but it's only shown in `CourseNextNode`. Making it more prominent (e.g., color-coding difficulty) would help students plan balanced semesters.
- [ ] **Backend-driven career list** — the 3 careers are hardcoded in `CareerSelector.jsx`. If you add careers to the DB, the selector should fetch them dynamically.

## Quick Wins

- [ ] **Keyboard shortcuts** — `E` for edit mode, `P` for projection, `Esc` to deselect. ReactFlow supports this natively.
- [x] **Responsive layout for mobile** — the graph currently assumes desktop. Even basic pinch-to-zoom and smaller node sizing would make it usable on phones.
- [ ] **Loading skeletons** — replace the blank screen while courses load with a skeleton placeholder that matches the graph layout.
