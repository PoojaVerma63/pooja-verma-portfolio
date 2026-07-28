# Pooja Verma — Portfolio Website

Personal portfolio built as two independent apps: an **Angular 18** front end and an **ASP.NET Core 8** Web API back end. The frontend fetches all resume content (profile, skills, experience, projects, education, certifications) from the API at runtime, so updating your resume never requires touching Angular code.

**Live demo:** _add your deployed URL here_

---

## Tech Stack

| Layer      | Technology |
|------------|------------|
| Frontend   | Angular 18 (standalone components), TypeScript, SCSS |
| Backend    | ASP.NET Core 8 Web API, C# |
| API Docs   | Swagger / OpenAPI |
| Styling    | Custom design system ("System Architecture" theme) using CSS variables |

---

## Project Structure

```
pooja-portfolio-project/
├── backend/
│   └── PortfolioApi/
│       ├── Controllers/       # PortfolioController.cs, ContactController.cs
│       ├── Models/             # C# models (Profile, Experience, Project, etc.)
│       ├── Data/               # PortfolioData.cs — your resume content lives here
│       ├── Program.cs          # App startup, CORS, Swagger
│       └── appsettings.json
│
└── frontend/
    └── src/
        ├── app/
        │   ├── components/     # navbar, hero, about, skills, experience,
        │   │                    # projects, education, contact, footer
        │   ├── models/          # TypeScript interfaces (mirror the C# models)
        │   ├── services/        # portfolio.service.ts — all HTTP calls
        │   └── app.component.*
        ├── environments/        # API URLs for local vs. production
        └── styles.scss          # global design tokens
```

---

## Prerequisites

- [.NET 8 SDK](https://dotnet.microsoft.com/download)
- [Node.js 18+](https://nodejs.org) and npm
- Angular CLI: `npm install -g @angular/cli`

---

## Getting Started

### 1. Run the backend

```bash
cd backend/PortfolioApi
dotnet restore
dotnet run
```

API runs at `https://localhost:7050`. Open `https://localhost:7050/swagger` to test endpoints directly.

### 2. Run the frontend

```bash
cd frontend
npm install
ng serve
```

Site runs at `http://localhost:4200` and automatically pulls content from the API.

---

## API Endpoints

| Endpoint                        | Method | Description                                  |
|----------------------------------|--------|-----------------------------------------------|
| `/api/portfolio/all`             | GET    | All portfolio data in one response            |
| `/api/portfolio/profile`         | GET    | Name, title, contact info, summary            |
| `/api/portfolio/skills`          | GET    | Skill groups                                   |
| `/api/portfolio/experience`      | GET    | Work history                                   |
| `/api/portfolio/projects`        | GET    | Key projects                                   |
| `/api/portfolio/education`       | GET    | Education entries                              |
| `/api/portfolio/certifications`  | GET    | Certifications and training                    |
| `/api/contact`                   | POST   | Accepts `{ name, email, subject, message }`   |

---

## Updating Your Content

All resume content lives in one file:

```
backend/PortfolioApi/Data/PortfolioData.cs
```

Edit the `Profile`, `Skills`, `Experience`, `Projects`, `Education`, or `Certifications` lists there and restart the API — no Angular changes needed.

To change colors, fonts, or spacing, edit the CSS variables in:

```
frontend/src/styles.scss
```

---

## Deployment

- **Backend:** `dotnet publish -c Release`, then host on Azure App Service, Render, or Railway.
- **Frontend:** `ng build --configuration production`, then deploy the `dist/` folder to Netlify, Vercel, or Azure Static Web Apps.
- Before building for production, update `frontend/src/environments/environment.prod.ts` with your live API URL, and update the CORS policy in `Program.cs` to allow your live frontend domain.

---

## Roadmap

- [ ] Move resume data from static C# lists to SQL Server via Entity Framework Core
- [ ] Send real emails from the contact form (SMTP / SendGrid)
- [ ] Add a resume PDF download button
- [ ] Add unit tests (xUnit for the API, Jasmine/Karma for Angular)
- [ ] Custom domain

---

## Author

**Pooja Verma** — Full Stack .NET Developer
📧 pv150489@gmail.com · 📞 6388943172 · [LinkedIn](https://linkedin.com/in/pooja-verma-aa0150239)
