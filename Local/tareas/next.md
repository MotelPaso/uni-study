# App — Next Steps

> Feedback from program director review. He liked the app and outlined the following areas to move forward.

---

## 1. Research: Search Spaces for Academic Projection

The app needs to make academic projections based on the courses a student has taken. Before building this feature, research is needed on how to define and navigate the **search space** for these projections.

**Things to explore:**

- What defines a valid academic projection? (prerequisites met, credit load, graduation requirements)
- How to represent the course graph (DAG of prerequisites)
- Search/planning algorithms suitable for this space (e.g. BFS/DFS over the course graph, constraint satisfaction, heuristic search)
- Whether to use rule-based logic, ML-based recommendations, or a hybrid approach
- Existing academic advising systems or research papers to reference

---

## 2. Backend Development

The app currently lacks a backend. A server-side layer is needed to support data persistence, business logic, and eventually the projection engine.

**Things to define:**

- Stack choice (e.g. Node/Express, FastAPI, Django)
- Database design (students, courses, prerequisites, enrollment history)
- API endpoints the frontend will consume
- Where the projection/recommendation logic will live
- Authentication and data handling if the app will have user accounts

---

## Status

- [ ] Research search spaces for academic projection
- [ ] Define backend stack and architecture
- [ ] Design database schema
- [ ] Build initial API