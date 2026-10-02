# Gabriel Paes de Carvalho

Backend Developer · .NET / C# · Santarém, Portugal

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/gabriel-paes-carvalho)

---

I build **Web APIs with ASP.NET Core**. By day I'm a Junior Backend Developer sharing a .NET codebase with another developer. Outside that, I keep personal projects to push into what the job doesn't cover yet — layered separation, JWT, asynchronous processing and automated testing.

What I care about: someone else should be able to clone the repo, run it and change it without asking me anything. In practice that means consistent validation, predictable HTTP responses, and a README that explains the decisions instead of listing the files.

Open to backend .NET roles around **Santarém, Greater Lisbon or Coimbra** — remote, hybrid or on-site.

---

## Stack

| Area | Technologies |
|:---|:---|
| **Language** | C# (.NET 8 / .NET 10) |
| **Web** | ASP.NET Core — Minimal APIs and Web API |
| **Data** | Entity Framework Core, SQL Server, code-first migrations |
| **Security** | JWT Bearer, role-based authorisation, PBKDF2 password hashing |
| **Design** | Layered separation, Dependency Injection, Outbox pattern |
| **Testing & docs** | xUnit, OpenAPI / Scalar |
| **Tooling** | Git, GitHub, Azure DevOps |

---

## Featured project — [Authdoc](https://github.com/gcarvalhomain/Authdoc)

Identity and access API for a document platform aimed at immigrants. The central guarantee is simple: **each user reaches only their own documents**. So the project starts at the identity layer, because everything else depends on it.

| Built | Decision behind it |
|:---|:---|
| JWT issuing and validation | HMAC-SHA256, with issuer, audience, lifetime and signature checked on every request |
| Role-based authorisation | An `Admin` policy guards the administrative routes, and `Role` is not writable through the update endpoint, so a payload cannot escalate privilege |
| Password hashing | PBKDF2 with a random salt via the ASP.NET Core password hasher, with format versioning so hashes can be rehashed as the algorithm evolves |
| Idempotent bootstrap | Pending migrations and the first admin are applied at startup, solving the chicken-and-egg problem of an admin-only registration endpoint, safely on every run |
| GUID identifiers | No sequential enumeration of resources, which matters once those resources are personal documents |

The repo documents the reasoning in full, including what is **not** built yet and why. Next: the documents module with resource-based authorisation, and integration tests with xUnit and `WebApplicationFactory`.

---

## Currently learning

| Focus | What that means in practice |
|:---|:---|
| **Automated testing** | xUnit and integration tests with `WebApplicationFactory` |
| **Reading code critically** | Following an execution flow to the root cause instead of guessing |
| **Docker and CI/CD** | Containerising an API and wiring a GitHub Actions pipeline |

---

Happy to talk about .NET, opportunities or collaboration — [LinkedIn](https://www.linkedin.com/in/gabriel-paes-carvalho)
