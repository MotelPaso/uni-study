# Code Improvements Checklist

## 1. Move All Supabase Calls to Backend

The frontend currently queries Supabase directly in 3 places. These should all go through FastAPI to keep a single data access layer.

- [ ] **1a.** `getCoursesBase()` in `frontend/src/services/API.js:44-60` — queries `courses` and `prerequisites` tables directly from the browser. Move to the existing `/courses` backend endpoint or create a new one.
- [ ] **1b.** `getMinors()` in `frontend/src/services/API.js:98-101` — queries the `minors` table directly. Add a `/minors?career=...` endpoint to FastAPI.
- [ ] **1c.** Once all queries go through the backend, remove `@supabase/supabase-js` from `frontend/package.json` and delete `frontend/src/services/supabase.js`.
### Response:
The frontend must fetch courses through Supabase due to limitations on the backend; the backend loads later that the frontend, it's a known issue and it probably won't be fixed.

---

## 2. Delete Dead Code / Unused Files

- [x] **2a.** Delete `frontend/src/components/CourseNode.jsx` — exported but never imported. Only `CourseNextNode` is used as the ReactFlow node type.
- [x] **2b.** Delete `frontend/src/components/CourseMain.jsx` — never imported anywhere.
      It will be used later.
- [x] **2c.** Delete `frontend/src/data/courses.js` — 1,357 lines of hardcoded course data, never imported. The app fetches from the API/Supabase.
- [x] **2d.** Delete `frontend/src/data/ICCI.json` — 8,770 lines, never imported.
- [x] **2e.** Delete `backend/data/ICCI.json` — duplicate, also never imported.
		Kept if we need to migrate the database.
- [x] **2f.** Remove `getCourseData()` from `frontend/src/services/API.js:23-40` — exported but never called anywhere.
		Legacy function from when backend was stored on a local server, must be kept in case we have to go back to the legacy system, a comment has been placed for future debugging. 
- [x] **2g.** Delete `backend/vite.config.js` — frontend config file misplaced in the backend directory.
- [x] **2h.** Delete `backend/testing/proyection.py` — standalone test with hardcoded data, duplicates logic in `connection.py`.

---

## 3. Remove Unused Imports / Variables

- [x] **3a.** `frontend/src/components/CourseNextNode.jsx:2` — remove `FaAngleDown` import.
- [x] **3b.** `frontend/src/CurriculumGraph.jsx:18` — remove `SiConcourse` import.
- [x] **3c.** `frontend/src/components/BotBar.jsx:2-5` — remove `VscEditSparkle`, `GrPlan`, `TbFocusCentered`, `RiResetLeftLine` imports.
- [x] **3d.** `frontend/src/components/TopBar.jsx:2` — remove `RiArrowLeftSLine` import.
- [x] **3e.** `frontend/src/components/TopBar.jsx:1,6` — remove `useState` import and the `showMessage`/`setShowMessage` state (never used).
- [x] **3f.** `frontend/src/App.jsx:5` — remove `getMinors` import (not called in this file).
- [x] **3g.** `frontend/src/CurriculumGraph.jsx:113` — remove `setMinorId` from props destructuring (never used, never passed from App).

---

## 4. Extract Duplicated Code

- [x] **4a.** `buildGraph()` is nearly identical in `CurriculumGraph.jsx:42-88` and `ProyectionGraph.jsx:37-103`. Extract to a shared utility file (e.g., `frontend/src/utils/buildGraph.js`).
		Both do fundamentally different things, cannot be extracted to a shared utility.
- [x] **4b.** `SEMESTER_WIDTH` and `COURSE_HEIGHT` constants are duplicated in `CurriculumGraph.jsx:25-26` and `ProyectionGraph.jsx:7-8`. Move to a shared constants file.
		Only used in two graphs and they may differ in the future, not moved.
- [x] **4c.** Theme toggle button (moon/sun icons) is duplicated in `TopBar.jsx:20-25` and `CareerSelector.jsx:63-66`. Extract to a shared `<ThemeToggle>` component. 
- [x] **4d.** `theme == "light" ? "black" : "white"` is repeated in 4+ places across `BotBar.jsx`, `TopBar.jsx`, `ProyectionGraph.jsx`, `CareerSelector.jsx`. Create a helper function or use CSS variables.
		Changed on CareerSelector and BotBar, all other has breaking issues.
- [x] **4e.** `DB_CONFIG` dict is copy-pasted in `backend/connection.py:8-15`, `backend/data/workdata.py:8-15`, and `backend/data/test_connection.py:6-13`. Import from a single source.
- [ ] **4f.** Prerequisite-mapping logic is duplicated in `backend/connection.py` between `getCourses()` (lines 46-51) and `getMinorCourses()` (lines 91-93). Extract a shared helper.

---

## 5. Bug Fixes

- [x] **5a.** `frontend/src/components/BotBar.jsx:66` — `setProgress((prev) => "")` resets progress to an empty string instead of `{}`. This breaks all `progress[course.code]` lookups.
- [x] **5b.** `frontend/src/CurriculumGraph.jsx:125-128` — `useMemo` for `buildGraph` is missing `theme` in its dependency array. Causes stale node colors when theme toggles.
- [ ] **5c.** `frontend/src/CurriculumGraph.jsx:198` — `useEffect([career])` calls `setOriginalCourses(courses)` but `courses` (a prop) is not in the dependency array. Uses stale value.
- [x] **5d.** `frontend/src/CurriculumGraph.jsx:216-218` — `handleSendProgress` reads from `localStorage` instead of using the `progress` React state, creating state desync.
- [x] **5e.** `frontend/src/App.jsx:15-18` — `JSON.parse(saved)` from localStorage has no try/catch. Malformed data crashes the app on startup.
- [x] **5f.** `backend/connection.py:110` — `DISPERSION_LIMIT = 2` is redefined, shadowing the module-level definition on line 20.

---

## 6. Add Error Handling

- [ ] **6a.** `CurriculumGraph.jsx:216-238` — `handleSendProgress` has no try/catch. If the API throws, `setLoadingProyection(false)` never runs and the UI stays in loading state forever.
- [ ] **6b.** `CurriculumGraph.jsx:240-255` — `handleMinorChange` same issue, no try/catch.
- [ ] **6c.** `CurriculumGraph.jsx:188-195` — `fetchMinors()` has no try/catch wrapper.
		CurriculumGraph needs a big refactor,  these functions will probably be deleted/changed later
- [x] **6d.** `CareerSelector.jsx:24` — `wakeBackend()` is called without `await`, errors silently swallowed.
		This is intended, it's a helper function to wake up the backend from its deep sleep state.
- [ ] **6e.** `backend/connection.py:26-27, 65-66` — `psycopg2.connect()` has no try/except. DB failure returns a raw 500 error with a stack trace.
- [ ] **6f.** Backend has no connection pooling — every request opens and closes a new DB connection. Add `psycopg2.pool` or similar.

---

## 7. Remove Console Logs

- [x] **7a.** `CurriculumGraph.jsx:94` — `console.table(minorBySemester)`
- [x] **7b.** `CurriculumGraph.jsx:248` — `console.log(result)`
- [ ] **7c.** `API.js:79` — `console.log(error)`
- [ ] **7d.** `API.js:90` — `console.log(".")`
- [ ] **7e.** `API.js:92` — `console.log(error)`
- [x] **7f.** `API.js:103` — `console.table(minors)`
- [x] **7g.** `API.js:118` — `console.table(response.data)`
- [x] **7h.** `backend/connection.py:16` — `print("DB_HOST:", ...)` — **security issue**, leaks DB host to stdout
- [ ] **7i.** `backend/connection.py:28` — `print("Connected!")`

---

## 8. Code Organization

- [ ] **8a.** `CurriculumGraph.jsx` (340 lines) handles graph rendering, minor selection, progress tracking, projection calls, and error display. Split into smaller components or custom hooks (e.g., `useProjection`, `useMinors`, `useProgress`).
- [ ] **8b.** Extract `buildGraph`, `applyMinorToCourses`, `MINOR_CODES`, and `TYPES_PROGRESS` from `CurriculumGraph.jsx` into separate utility and constants files.
- [ ] **8c.** `backend/connection.py` mixes DB helpers, caching, and the projection algorithm in one file. Extract the projection logic (`getProyeccion` and its helpers) to its own module.
- [x] **8d.** `backend/data/` contains seed scripts and test files mixed together. Reorganize into `scripts/` or `migrations/`.

---

## 9. Fix Loose Equality (`==` to `===`)

- [x] **9a.** `CurriculumGraph.jsx:222` — `status == "ongoing"`
- [x] **9b.** `CurriculumGraph.jsx:279` — `prev?.id == node.id`
- [x] **9c.** `ProyectionGraph.jsx:148` — `theme == "light"`
- [x] **9d.** `CareerSelector.jsx:65` — `theme == "light"`
- [x] **9e.** `BotBar.jsx:29` — `theme == "light"`
- [x] **9f.** `TopBar.jsx:17` — `theme == "light"`
- [x] **9g.** `TopBar.jsx:24` — `theme == "light"`

---

## 10. Add Missing Memoization

- [ ] **10a.** `App.jsx:23-27` — wrap `toggleTheme` in `useCallback`.
- [ ] **10b.** `CurriculumGraph.jsx:266-284` — `onNodeClick` and `onPaneClick` are inline arrows in JSX. Extract to `useCallback` to prevent unnecessary ReactFlow re-renders.
- [ ] **10c.** `BotBar.jsx:31-34` — wrap `resetAll` in `useCallback`.

---

## 11. Security Fixes

- [x] **11a.** `backend/connection.py:16` — remove `print("DB_HOST:", ...)` that leaks DB host to stdout.
- [ ] **11b.** `backend/main.py:10` — move hardcoded private IP `100.102.126.109` in CORS origins to an environment variable.
- [ ] **11c.** `frontend/src/services/supabase.js:3-4` — add validation for `VITE_SUPABASE_URL` and `VITE_SUPABASE_PUBLISHABLE_KEY` before passing to `createClient`.
- [x] **11d.** `backend/main.py:28` — validate the `career` parameter against allowed values instead of passing it directly to the query.

---

## 12. Style / Minor Improvements

- [x] **12a.** `CourseNode.jsx` uses 100+ lines of inline styles — convert to Tailwind classes (moot if file is deleted per 2a).
- [x] **12b.** `API.js` mixes `export async function` and `export const` arrow functions. Pick one style.
- [ ] **12c.** Python backend uses `camelCase` function names (`getCourses`, `checkDispersion`). PEP 8 recommends `snake_case`.
- [ ] **12d.** `MinorToggle.jsx:30` — `key={0}` alongside `key={m.id}`, inconsistent React key usage.
