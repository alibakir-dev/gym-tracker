# ROADMAP: PulseLog — Gamified Gym & TDEE Tracker v1.0.0

Build a gamified, full-stack workout and adaptive TDEE tracker using **TypeScript, React, Tailwind CSS, Node.js (Express), PostgreSQL (Neon), and Drizzle ORM**.

> Save as `ROADMAP.md` in the root of the `gym-tracker` repo.
> Progress is not tracked in a file. The coach finds the current milestone by checking which "Done when" items are already true in the repo.

---

## 1. Tech Stack & Curriculum Mapping (Locked)

| Layer                         | Technology                                                                                                                   | Curriculum Tier & Phase |
| ----------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ----------------------- |
| **Language**                  | TypeScript (`strict: true`) + ES6+                                                                                           | T1 — P1 & P2            |
| **Frontend Core**             | React + Vite + React Router (5 core routes + Auth)                                                                           | T1 — P2                 |
| **Styling & Design**          | **Tailwind CSS** (configured with PulseLog Kinetic Mono theme tokens + `Roboto Mono` global font) + WCAG Accessibility       | T1 & T2 — P2 & P4       |
| **State & Data Fetching**     | TanStack Query (server state) + Zustand (UI/timer/theme client state)                                                        | T2 — P2                 |
| **Forms & Validation**        | React Hook Form + Zod (shared validation schemas)                                                                            | T1 & T2 — P2 & P3       |
| **Frontend Testing**          | Vitest + React Testing Library                                                                                               | T1 — P2                 |
| **Backend Core**              | Node.js + Express (REST API design) + Zod server validation                                                                  | T1 — P3                 |
| **Authentication & Security** | Session-based auth (`HttpOnly` cookie) + `argon2` hashing + OWASP Top 10 / IDOR checks (plus conceptual JWT comparison)      | T1 — P3                 |
| **Database & ORM**            | PostgreSQL (hosted on **Neon**) + **Drizzle ORM** & migrations + SQL (`JOIN`, `GROUP BY`, `index`, `EXPLAIN`, `transaction`) | T1 — P3                 |
| **Backend Testing**           | Supertest (integration tests for API routes)                                                                                 | T1 — P3                 |
| **Deployment**                | Vercel (Frontend), Render (Backend), Neon (Serverless Postgres), `.env` management                                           | T1 — P1–P3              |

---

## 2. Application Routes & Features (`React Router`)

1. **Persistent Floating Pill Navbar (`max-width: 1120px`):**
   - Brand logo (`PULSELOG`), Level & XP pill (`LVL 12 • 2,450 XP`), 5 route links (`Dashboard`, `Workouts`, `Nutrition`, `Profile`, `Settings`), Streak pill, and Theme toggle (`Dark` default / `Light`).
2. **`/ (DashboardPage)` — Daily Command Center:**
   - Personalized greeting, primary CTA (`Log a workout +`), **Muscle Balance Analyzer Card** (horizontal progress bars per muscle group + `#FFF0EB` / `#2A1A1A` advisory box flagging neglected muscles like Rear Delts/Hamstrings), and **Today's Snapshot Card**.
3. **`/workouts (WorkoutsPage)` — Movement Logger & Plate Calculator:**
   - Multi-set workout logger (`React Hook Form + Zod`), automatic **Estimated 1RM** (Epley formula), Relative Strength (`BW Ratio`), active rest timer (`Zustand`), and visual **Barbell Plate Calculator**.
4. **`/nutrition (NutritionPage)` — TDEE, 14-Day Calibration & Rolling Weight Engine:**
   - Formula BMR/TDEE summary cards (from Settings biometrics).
   - **14-Day Calibration Gate:** Until the user logs 14 days of morning weigh-ins and calories, displays an advisory progress banner (`"Keep logging your weight under the exact same conditions for 2 weeks (X/14 days) for us to calculate an accurate adaptive TDEE chart for you"`). Once `>= 14` logs exist, unlocks the **Adaptive TDEE & 7/14-Day Rolling Weight Trend Chart** (spreadsheet logic).
5. **`/profile (ProfilePage)` — Dedicated RPG Character, Badges, Gallery & Leaderboard:**
   - Player Level/XP banner & Relative Strength score.
   - **Achievement Badge Vault** (`100kg Bench Club`, `1.5x BW Squat`, `14-Day Calibration Complete`).
   - **Friends Leaderboard** ranked fairly by Relative Strength (`BW Ratio`) and Total XP.
   - **Then vs. Now Transformation Card** (side-by-side Week 1 vs. Week 4/12 comparison).
6. **`/settings (SettingsPage)` — Dedicated Biometrics, Split & Account Configuration:**
   - Biometric inputs (Age, Sex, Height, Activity Multiplier, Goal Deficit/Surplus) that feed the TDEE calculator.
   - Sport & Routine Movement selector that feeds the Muscle Balance Analyzer.
   - Unit (`KG/LBS`), Theme (`Dark/Light`), and Session `Log Out` controls.
7. **`/auth (AuthPage)` — Login & Registration:**
   - Session-based login and registration forms validated with `React Hook Form + Zod`.

---

## 3. Target Repository Structure

```
gym-tracker/
  client/                           # React + TypeScript + Tailwind CSS (Vite) frontend (Deploy: Vercel)
    index.html
    tsconfig.json                   # strict: true
    vite.config.ts
    src/
      main.tsx
      App.tsx                       # React Router (6 routes) + QueryClientProvider
      index.css                     # Tailwind directives + PulseLog theme CSS variables (dark + light) + Roboto Mono
      types/
        index.ts                    # strict TypeScript interfaces
      schemas/
        validation.ts               # Zod schemas for auth, settings, daily logs, workouts
      utils/
        calculations.ts             # BMR, TDEE, 14-day calibration check, rolling avg, 1RM, plates
        muscleAnalyzer.ts           # exercise-to-muscle map & imbalance detector
        badgeEngine.ts              # XP and achievement unlock evaluator
        calculations.test.ts        # Vitest unit tests for all formulas & 14-day calibration
      store/
        useUiStore.ts               # Zustand store (theme, rest timer, unit preference)
      pages/
        AuthPage.tsx
        DashboardPage.tsx
        WorkoutsPage.tsx
        NutritionPage.tsx
        ProfilePage.tsx
        SettingsPage.tsx
      components/
        PillNavbar.tsx
        MuscleBalanceCard.tsx
        CalibrationBanner.tsx
        PlateCalculatorCard.tsx
        BadgeVaultCard.tsx
        TransformationCard.tsx
        LeaderboardCard.tsx
  server/                           # Node.js + Express + TypeScript backend (Deploy: Render)
    tsconfig.json                   # strict: true
    drizzle.config.ts               # Drizzle Kit configuration
    src/
      index.ts
      app.ts                        # Express app, CORS, HttpOnly session cookie middleware
      db/
        index.ts                    # Neon PostgreSQL connection + Drizzle instance
        schema.ts                   # Drizzle tables + indexes (users, user_settings, daily_logs, workouts, workout_sets, user_badges, friendships)
        migrations/                 # SQL migrations generated by Drizzle Kit
      middleware/
        requireAuth.ts              # Session check + IDOR authorization guard
        validate.ts                 # Zod request validation middleware
      routes/
        auth.ts                     # argon2 password hashing + HttpOnly session cookie
        settings.ts                 # GET/PUT biometrics & routine movement split
        nutrition.ts                # CRUD for daily weight/calorie logs & calibration status
        workouts.ts                 # CRUD + DB transaction for workout + sets + XP update
        profile.ts                  # Badges, transformation checkpoints & SQL JOIN leaderboard
      tests/
        api.test.ts                 # Supertest integration tests
  design/
    spec.md                         # PulseLog Kinetic Mono specification + Roboto Mono
    screenshots...
  .github/
    copilot-instructions.md
  GEMINI.md
  README.md
  .gitignore
  ROADMAP.md
```

---

## 4. Milestones

Each milestone is one **branch**, several **commits**, one **pull request**.

### M0: Initial repository setup and `design/spec.md` (about 1.5 h)
- **Branch:** `main` (initial repo setup only)
- **Tasks:** Save `design/spec.md` and put Google Stitch Desktop Dark Mode screenshots in `design/`. Add `.gitignore` and `README.md`, push to GitHub, enable branch protection on `main`, and update the `portfolio` site's Gym Tracker card from `Planned` to `In progress`.
- **Done when:** `design/spec.md`, `README.md`, and `.gitignore` are on `main` and branch protection is active.

### M1: Vite + React + TypeScript (`strict`), Tailwind CSS Theme & 5-Page Router Shell (about 2.5 h)
- **Branch:** `feat/ts-tailwind-shell`
- **Tasks:** Scaffold `client/` (`react-ts`, `"strict": true`), load `Roboto Mono` from Google Fonts, install and configure **Tailwind CSS** with custom theme tokens mapped to `design/spec.md` (Dark default `#090916`/`#181824` and Light `#F3F6F9`/`#FFFFFF`, coral `#FF5A36`, emerald `#10B981`, `10px` card radius, `9999px` pill radius), set up `useUiStore.ts` (`Zustand`), build `PillNavbar.tsx`, and wire the 6 routes (`Dashboard`, `Workouts`, `Nutrition`, `Profile`, `Settings`, `Auth`).
- **Done when:** TypeScript compiles cleanly, Tailwind custom theme classes work in both Dark and Light modes, and all 5 nav pills switch pages.

### M2: Spreadsheet Math, 14-Day Calibration Engine & `Vitest` Unit Tests (about 3 h)
- **Branch:** `feat/calculation-engine-vitest`
- **Tasks:** Build `src/utils/calculations.ts`: Mifflin-St Jeor BMR & TDEE, `getCalibrationStatus(logs)` (returns days remaining out of 14 and locks adaptive chart until 14 logs exist), 7-day & 14-day rolling weight average, adaptive TDEE calculation from real weight delta, Epley 1RM, Relative Strength (`BW Ratio`), and Barbell Plate breakdown. Write unit tests in `calculations.test.ts` with **Vitest**.
- **Done when:** All formulas and the 14-day calibration gate pass 100% of Vitest unit tests.

### M3: `SettingsPage` & `DashboardPage` (Muscle Balance Analyzer + RTL Test) (about 3 h)
- **Branch:** `feat/settings-dashboard-analyzer`
- **Tasks:** Build `SettingsPage.tsx` (`React Hook Form + Zod` for biometrics and movement split selection) and `DashboardPage.tsx` with `MuscleBalanceCard.tsx` (mapping chosen movements to muscle groups and showing the `#FFF0EB` / `#2A1A1A` advisory box when Rear Delts/Hamstrings or Push/Pull ratio are neglected). Write a **React Testing Library** test for the imbalance warning.
- **Done when:** Updating movements in Settings updates the Dashboard muscle bars and passes the RTL test.

### M4: `NutritionPage` — 14-Day Calibration Banner & Rolling Weight Table (about 3 h)
- **Branch:** `feat/nutrition-calibration-page`
- **Tasks:** Build `NutritionPage.tsx` using `React Hook Form + Zod` and Tailwind CSS. Render BMR/TDEE cards, `CalibrationBanner.tsx` (`"Keep logging your weight under the exact same conditions for 2 weeks (X/14 days)..."` when `< 14` logs), the 7-day rolling weight table, and the unlocked Adaptive TDEE chart once `>= 14` days are logged.
- **Done when:** Logging entries increments calibration progress and unlocks the full adaptive trend view at 14 entries.

### M5: `WorkoutsPage` & `ProfilePage` (Logger, Plate Calculator, Badges & Gallery) (about 3.5 h)
- **Branch:** `feat/workouts-profile-pages`
- **Tasks:** Build `WorkoutsPage.tsx` (set/rep/weight form, live Epley 1RM, `Zustand` rest timer, and `PlateCalculatorCard.tsx`) and `ProfilePage.tsx` (`BadgeVaultCard.tsx`, `TransformationCard.tsx` for Week 1 vs. Week 12 comparison, and `LeaderboardCard.tsx` shell).
- **Done when:** Logging a 100kg bench press calculates 1RM, awards XP, and unlocks the badge on the Profile page.

### M6: PostgreSQL on Neon & Drizzle ORM Schema + Migrations (about 3 h)
- **Branch:** `feat/neon-drizzle-schema`
- **Tasks:** Create a PostgreSQL database on **Neon**. Initialize `server/` with TypeScript, Express, and **Drizzle ORM**. Define tables and indexes in `src/db/schema.ts` (`users`, `user_settings`, `daily_logs`, `workouts`, `workout_sets`, `user_badges`, `friendships`), generate migrations with `drizzle-kit`, and apply them to Neon.
- **Done when:** All tables and indexes are live on Neon PostgreSQL via Drizzle migrations.

### M7: Session Auth (`argon2` + `HttpOnly` Cookie) & OWASP / IDOR Security (about 3.5 h)
- **Branch:** `feat/session-auth-security`
- **Tasks:** Implement `/api/auth` routes with **`argon2`** password hashing, **`HttpOnly` session cookies**, **Zod** server validation, and `requireAuth.ts` middleware preventing **IDOR** (cross-user data access).
- **Done when:** Auth endpoints and IDOR guards work securely with `401`/`403` protection.

### M8: REST API, SQL Transactions, `JOIN`/`GROUP BY` & `Supertest` (about 3.5 h)
- **Branch:** `feat/rest-api-supertest`
- **Tasks:** Implement `/api/settings`, `/api/nutrition`, `/api/workouts` (wrapped in a database **transaction**), and `/api/profile/leaderboard` (using SQL **`JOIN`**, **`GROUP BY`**, and **`EXPLAIN`**). Write integration tests using **Supertest**.
- **Done when:** All routes pass Zod validation and `Supertest` integration tests.

### M9: Full-Stack Integration with `TanStack Query` (about 3 h)
- **Branch:** `feat/tanstack-query-integration`
- **Tasks:** Connect all 6 frontend pages to the Express + Neon backend using **`TanStack Query` (`useQuery`, `useMutation`, `invalidateQueries`)**.
- **Done when:** Biometrics, 14-day nutrition logs, workouts, badges, and leaderboard data persist end-to-end in PostgreSQL.

### M10: WCAG Accessibility, Responsive Polish & Lighthouse (about 2 h)
- **Branch:** `fix/wcag-responsive-polish`
- **Tasks:** Audit all 5 pages at 375px, 768px, 1024px, and 1440px. Verify mobile pill-menu collapse at `1024px`, keyboard navigation, 4.5:1 contrast in Dark/Light modes, and Lighthouse scores >= 95.
- **Done when:** Zero horizontal overflow and Lighthouse mobile scores meet 95+.

### M11: Deploy to Vercel + Render + Neon & Release `v1.0.0` (about 2 h)
- **Branch:** `chore/deploy-production`
- **Tasks:** Deploy backend to **Render**, frontend to **Vercel**, connect **Neon**, write `README.md`, tag `v1.0.0`, publish GitHub Release, and update the `portfolio` site with the live link.
- **Done when:** Production app is live, `v1.0.0` is released, and `portfolio` links to it.