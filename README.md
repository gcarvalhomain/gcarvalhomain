# Gabriel Paes de Carvalho

Backend Developer · .NET / C# · Santarém, Portugal

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/gabriel-paes-carvalho)
[![Email](https://img.shields.io/badge/Email-0078D4?style=flat-square&logo=microsoftoutlook&logoColor=white)](mailto:gabriel.p.carva@outlook.com)

---

I build and document **Web APIs with ASP.NET Core**.

By day I'm a Junior Backend Developer sharing a .NET codebase with another developer — branches, pull requests and code review, day in and day out. Outside that I keep personal projects to push into what the job doesn't cover yet: session security, automated testing and a deployment pipeline I own end to end.

What I care about: someone else should be able to clone the repo, run it and change it without asking me anything. In practice that means consistent validation, predictable HTTP responses, and a README that explains the decisions instead of listing the files.

Open to backend .NET roles around **Santarém, Greater Lisbon or Coimbra** — remote, hybrid or on-site.

---

## Stack

| Area | Technologies |
| :--- | :--- |
| **Language** | C# (.NET 8 / .NET 10) |
| **Web** | ASP.NET Core — Minimal APIs and Web API |
| **Data** | Entity Framework Core 10, SQL Server, code-first migrations |
| **Security** | JWT Bearer, refresh token rotation, role-based authorisation, PBKDF2 hashing, rate limiting |
| **Design** | Layered separation, Dependency Injection, global exception handling |
| **Testing** | xUnit, `WebApplicationFactory`, EF Core InMemory |
| **CI/CD & docs** | Azure Pipelines, Azure App Service, OpenAPI / Scalar |
| **Tooling** | Git, GitHub, Azure DevOps |

---

## Featured project: [Authdoc](https://github.com/gcarvalhomain/Authdoc)

Identity and access API for a document platform aimed at immigrants. The central guarantee is simple: **each user reaches only their own documents**. So the project starts at the identity layer, because everything else depends on it.

| Built | Decision behind it |
| :--- | :--- |
| Stateless JWT authentication | HMAC-SHA256, with issuer, audience, lifetime and signature checked on every request |
| Refresh token with rotation | Each use issues a new token and revokes the previous one, and only the SHA-256 hash is stored — a leaked database row cannot be replayed as a session |
| Role-based authorisation | An `Admin` policy guards the administrative routes, and `Role` is not writable through the update endpoint, so a payload cannot escalate privilege |
| Password hashing | PBKDF2 with a random salt via the ASP.NET Core password hasher, with format versioning so hashes can be rehashed as the algorithm evolves |
| Rate limiting | Login and password change are capped per IP and answer `429` beyond that, so the endpoints that guard credentials are not free to brute-force |
| Idempotent bootstrap | Pending migrations and the first admin are applied at startup, solving the chicken-and-egg problem of an admin-only registration endpoint, safely on every run |
| GUID identifiers | No sequential enumeration of resources, which matters once those resources are personal documents |

**Tested and shipped, not just written.** Unit tests cover the validation and user rules; integration tests drive the whole API over HTTP with `WebApplicationFactory` against an in-memory database, so they run with no SQL Server and no secrets. An Azure Pipelines workflow restores, builds in `Release`, runs those tests and deploys to Azure App Service — and a failing test stops the deploy.

The repo documents the reasoning in full, including what is **not** built yet and why. Next: the documents module, with ownership-based authorisation reusing this infrastructure.

---

## Also on here

| Project | What it is |
| :--- | :--- |
| **[LoudApi / VELO](https://github.com/gcarvalhomain/LoudApi)** | Authentication and user-management API behind a CS2 events and news page — JWT in an HttpOnly cookie, role-based authorisation, covered by smoke and endpoint tests |

---

## Currently learning

| Focus | What that means in practice |
| :--- | :--- |
| **Reading code critically** | Following an execution flow to the root cause instead of guessing |
| **Observability** | Structured logging and health checks, so a failure in production is diagnosable |

---

Happy to talk about .NET, opportunities or collaboration: [LinkedIn](https://www.linkedin.com/in/gabriel-paes-carvalho)
