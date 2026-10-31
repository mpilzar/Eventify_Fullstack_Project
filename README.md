# 🐾 PetCare: Pet Health Records & Lost-Pet Platform

A multi-role web platform for **pet health records, vet appointments, and lost-and-found pet reporting**. I designed it end to end in **Figma** and then built it as a **React + TypeScript** single-page application.

> Built as a 3-person team project for the *Human–Computer Interaction* course (2025–2026). The brief was to go from user research and high-fidelity Figma prototypes to a working frontend, with no real backend. Data is served by a mock REST API (`json-server`).

<!-- Optional: add a hero screenshot or GIF here, e.g.
![PetCare home page](docs/screenshots/home.png)
-->

**[🎨 Figma design](#)** · **[▶️ Run locally](#-getting-started)** · **[🔑 Demo accounts](#-demo-accounts)**

---

## ✨ Highlights

- **Design to code.** I designed every screen in Figma first, then implemented it as a production-style React app with consistent theming and components.
- **Three user roles, three experiences.** Pet owners, veterinarians, and anonymous members of the public each get their own dashboard, navigation, and permissions.
- **Role-based routing.** A `ProtectedRoute` component and a React Context auth layer gate 20+ routes by role, and the session persists in `localStorage`.
- **Real interaction patterns.** It includes an interactive availability calendar, a map-based location picker (Leaflet), multi-criteria search and filtering, save-as-draft workflows, and status lifecycles for reports and appointments.
- **Usability-first.** Forms validate inline with clear error messages, users confirm destructive actions, the app shows feedback for loading and empty states, and labels use plain language.
- **Localized UI.** The whole interface is in Greek, for the platform's target users.

---

## 👥 Who it's for & what they can do

### 🏠 Pet owners
- View a pet's **digital health booklet** (vaccinations and medical history by date)
- **Search for vets** and filter by species, years of experience, minimum rating, and free slots on a given date and time
- **Book appointments** on a vet's live availability calendar, then track and cancel them
- **Rate and review** vets after a completed visit
- **Report a lost pet** by dropping a pin on a map, save the report as a draft, and mark the pet as found later
- Report a **found pet** and view the full report history

### 🩺 Veterinarians
- Set **weekly availability** on a clickable hour-by-day grid
- **Accept or reject appointment requests**, filter them by pet type and status, and have past appointments marked complete automatically
- **Register new pets** by microchip, with a *temporary save* option for incomplete registrations
- Record **medical actions** and browse a pet's full **medical history**
- Manage **ownership**: assign a new owner, transfer ownership, or process an adoption
- See their **reviews and ratings** from owners

### 🌍 Public visitors (no account)
- Browse **lost pets** in their area
- Report a found pet, whether it's a **known pet** or an **unidentified animal**, with location on a map
- Search for vets

---

## 🛠️ Tech stack

| Area | Tools |
|---|---|
| **Design** | Figma (wireframes → high-fidelity prototypes) |
| **Framework** | React 19, TypeScript, Vite 7 |
| **UI** | Material UI (MUI v7) with a custom theme layer and Emotion |
| **Routing & state** | React Router v7, React Context API |
| **Maps** | Leaflet + React-Leaflet |
| **Dates & calendars** | react-big-calendar, date-fns, Moment.js |
| **Data** | Axios / Fetch → `json-server` mock REST API |
| **Tooling** | ESLint, typescript-eslint |

---

## 🧭 Design process

1. **User research & personas.** We identified three user groups with different goals: owners, vets, and the public.
2. **Task analysis.** We mapped the key tasks for each role, such as "book an appointment" and "report a lost pet", and their steps.
3. **Wireframes → hi-fi prototypes in Figma.** We built interactive prototypes covering every screen and flow.
4. **Implementation.** We turned the prototypes into React components and kept the design language consistent: shared theme, colors, typography, and iconography.
5. **Usability principles applied.** These include visibility of system status, error prevention and clear recovery, consistency across roles, and recognition over recall. For example, every dashboard is built from the same task cards.

<!-- Replace the link above and/or add Figma frame exports, e.g.
| Figma prototype | Implementation |
|---|---|
| ![](docs/figma/owner-dashboard.png) | ![](docs/screenshots/owner-dashboard.png) |
-->

---

## 🚀 Getting started

**Prerequisites:** Node.js 18+ and npm.

```bash
# 1. Clone and enter the app folder
git clone <this-repo-url>
cd PetCare-HCI-main/Pet-Care-platform

# 2. Install dependencies
npm install

# 3. Start the mock backend (serves db.json on port 3001)
npx json-server@0.17.4 --watch db.json --port 3001

# 4. In a second terminal, start the frontend
npm run dev
```

Then open the URL Vite prints, usually **http://localhost:5173**.

### 🔑 Demo accounts

| Role | Email | Password |
|---|---|---|
| Pet owner | `georgia@gmail.com` | `12345678` |
| Veterinarian | `kati3@gmail.com` | `12345678` |

As a vet, look up a pet by microchip **`CT555555555`** to open a sample pet profile and medical record.

---

## 📁 Project structure

```
Pet-Care-platform/
├── db.json                  # Mock database (users, pets, appointments, reports, reviews)
├── public/                  # Icons and illustrations
└── src/
    ├── App.tsx              # Route table (public / owner / vet)
    ├── context/AuthContext  # Auth state + session persistence
    ├── components/          # Navbar, ProtectedRoute, Map, ForgotPassword
    ├── shared-theme/        # MUI theme, light/dark mode, component overrides
    ├── api/                 # Login helpers against the mock API
    └── pages/
        ├── owner/           # Dashboard, booklet, appointments, vet search, reports
        ├── vet/             # Dashboard, availability calendar, requests, reviews
        │   └── pet/         # Registration, medical book/history, ownership flows
        ├── person/          # Public lost/found pet pages
        ├── sign-up/         # Owner & vet registration
        └── edit-profile/    # Profile editing
```

---

## ⚠️ Scope & limitations

This is a **frontend and interaction-design project**. The backend is intentionally out of scope.

- `json-server` stands in for a real API. Data is stored as plain JSON, and authentication is simulated: passwords are stored and compared in plain text, with no tokens.
- The "print booklet" actions are placeholders that confirm the action instead of producing a printable document.
- A production version would need a real backend with hashed credentials, server-side authorization, and input sanitization.

---

## 👩‍💻 Team

Built by a team of three:

- **Vasileios Zaritas**
- **Georgia Maria Valvi**
- **Alexandra Zormpa**

<!-- Optional: describe your own contribution, e.g.
**My role:** designed the vet-side flows in Figma and implemented the availability calendar, appointment-request management and ... 
-->

Original course repository: [alexandrazrmp/Pet-Care](https://github.com/alexandrazrmp/Pet-Care)
