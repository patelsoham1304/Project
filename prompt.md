ROLE: Act as a Senior Streamlit + Integration Engineer with 20+ years of 
experience in production-grade Python applications. This is a college BCA 
final-year project (3-member team), but follow real industry standards.

===========================================================
ACTIVE SKILLS & STYLE RULES
===========================================================
1. SKILL "ponytail" (installed, active): minimal, lazy-but-correct 
   solutions, no over-engineering, shortest working path.

2. MANUAL RULE "superpower" (not an installed skill, apply directly):
   - Validate all user inputs (empty, None, wrong type).
   - Specific exception types in try/except, never bare except.
   - Handle edge cases: empty lists, missing session_state keys, 
     zero-division in any percentage calculation.
   - Safety wins over brevity when they conflict.

3. MANUAL RULE "caveman" (not an installed skill, apply directly):
   - Comments in plain everyday English, no jargon.
   - Every function has a 1-2 line comment above it: what it does and why.
   - Blunt and direct, no fluff.

Priority if rules conflict: correctness/safety > works end-to-end > 
comment clarity.

===========================================================
PROJECT
===========================================================
Personalized Education Path Generator. Stack: Python 3.10+, Streamlit, 
pytest. I am Person 3 (UI + Integration). Person 1 built database/, 
Person 2 built modules/.

INPUTS YOU RECEIVE (read these FIRST, before writing anything):
- database/ (complete, from Person 1) and its INTERFACE.md
- modules/ (complete, from Person 2) and its INTERFACE.md
- The master spec document (Section 12 = Overall Progress % formula, 
  Section 20 = required pytest tests)

STEP 0 (MANDATORY, DO BEFORE CODING):
a) Read both INTERFACE.md files. List every modules/ function you will 
   call with its exact signature and return shape.
b) Locate the master spec, Section 12 and Section 20. If you cannot find 
   them in the project, STOP and ask me to paste them. Do NOT invent the 
   formula or the test list.
c) Confirm the real modules/ functions replace the old TEMP UI MOCKS. 
   Remove every `# TEMP UI MOCK` in the old ui/*.py files.
d) Show me a short plan and wait for my "go" only if a spec is missing. 
   Otherwise proceed.

===========================================================
YOUR SCOPE: STEP 4 + STEP 5 + STEP 6 + STEP 7
===========================================================
Files you OWN (create/modify only these):
  app.py
  ui/__init__.py
  ui/dashboard.py
  ui/profile_ui.py
  ui/career_ui.py
  ui/roadmap_ui.py
  ui/progress_ui.py
  ui/planner_ui.py
  tests/  (full pytest suite)
  docs/VIVA_DEMO_SCRIPT.md
  docs/PROGRESS_LOG.md
  README.md

Do NOT edit database/ or modules/. If you find a bug there, report it to 
me with file + line + suggested fix instead of changing it.

===========================================================
NAVIGATION (locked order, sidebar)
===========================================================
1. Dashboard (default)
2. Profile
3. Career & Skills
4. Roadmap
5. Progress
6. Study Planner
Plus a Student selector in the sidebar, stored in st.session_state.
Session state lives ONLY in ui/ and app.py, never in modules/ or database/.

===========================================================
UI RULES
===========================================================
- ZERO business logic in UI. Only call modules/ functions. Never import 
  from database/ directly. Never write raw SQL.
- Allowed Streamlit widgets ONLY: st.sidebar, form, selectbox, 
  multiselect, number_input, slider, progress, metric, expander, 
  dataframe, success/warning/error/info. (Layout basics like 
  st.title/st.header/st.write are fine; nothing exotic.)
- Wrap every modules/ call in try/except with a friendly st.error(). 
  No raw traceback ever reaches the browser.
- Handle ALL empty states gracefully with a helpful message (never a 
  crash or blank page):
    * no students exist yet
    * student has no career selected
    * student has no roadmap yet
    * student is "Career Ready" (nothing left to learn, show success)
- Overall Progress % MUST come from the modules/ function that 
  implements the Section 12 formula. Do not recompute it in the UI.
- Dashboard "Recent Activity" is built from PROGRESS.updated_at 
  (fetched via modules/).
- Dashboard "My Projects" is built from STUDENT_PROJECT (via modules/).

===========================================================
DELIVERABLES
===========================================================
1. The 7 UI files + app.py above.
2. Full pytest suite covering every test in master Section 20. Put in 
   tests/. Each test named after its Section 20 item so I can tick them 
   off. Use a temporary/test database so tests never touch real data.
3. docs/VIVA_DEMO_SCRIPT.md: a click-by-click path that takes under 
   5 minutes, using the Data Analyst walkthrough, with what to say at 
   each step.
4. README.md: overview, features, tech stack, folder structure, setup 
   (pip install + streamlit run app.py), how to run tests, team roles.
5. docs/PROGRESS_LOG.md: final log of what was built per step, decisions 
   made, known limitations.

===========================================================
ACCEPTANCE CRITERIA (verify by REAL execution, not by reading code)
===========================================================
- `pytest` runs and I see the real pass/fail output pasted back.
- `streamlit run app.py` starts with zero import errors, and the full 
  Data Analyst walkthrough completes without any error.
- No raw traceback appears anywhere in the UI.
- No `# TEMP UI MOCK` remains.
- No file outside "Files you OWN" was modified.

If your terminal tool cannot execute (path/shell issue), say so clearly 
and tell me exactly what you verified for real vs what I must click 
through myself. Do NOT claim PASS from code-reading alone.

===========================================================
GIT
===========================================================
Branch: feature/ui-integration. Commit style: feat: / test: / fix: / 
docs:. Small atomic commits per file or feature, not one giant commit.

===========================================================
OUTPUT FORMAT
===========================================================
- Work in this order: STEP 0 report, then app.py, then ui/ files in 
  nav order, then tests, then docs.
- After each file: (a) which modules/ functions it calls, (b) one 
  superpower example, (c) one caveman comment example.
- End with: real pytest output, real streamlit startup output, and a 
  short list of what I must still click through manually in the browser.