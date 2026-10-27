# Verifiable Records SaaS

A multi-tenant SaaS platform for issuing, verifying, and auditing digital credentials with optional blockchain anchoring.

## 🎯 Project Overview

This is a founder-led MVP (Minimum Viable Product) built over 12 weeks targeting recurring SaaS revenue. The platform enables organizations to issue tamper-evident digital credentials, allow third parties to verify them via QR codes, and maintain immutable audit trails.

**Key Principles:**
- ✅ Start with ordinary application first, add blockchain *only after* customer validation
- ✅ Focus on training/certification providers as the primary customer segment
- ✅ Build for multi-tenant isolation from day one
- ✅ No tokens, exchanges, or custom blockchain in year one
- ✅ Validate with 2 paid pilots before scaling

## 📊 12-Week Development Timeline

| Week | Focus | Deliverable |
|------|-------|-------------|
| 1-2 | Setup & Authentication | Working skeleton + login |
| 3-4 | Tenant Isolation & Authorization | Isolation tests pass |
| 5-6 | Credential Issuance & Verification | First signed credential |
| 7-8 | QR Codes & Public Verification UI | End-to-end demo |
| 9-10 | APIs, Rate Limits, Customer Integrations | Pilot-ready |
| 11-12 | Security Review & Production Launch | Live pilots |

## 🛠 Technology Stack

### Backend
- **Language:** Java 17+
- **Framework:** Spring Boot 3.x
- **Database:** PostgreSQL (managed)
- **Authentication:** OIDC Identity Provider
- **Cryptography:** SHA-256, Ed25519 (standard libraries)
- **Testing:** JUnit 5, Spring Boot Test, Testcontainers, Playwright

### Frontend
- **Framework:** React 18+
- **Language:** TypeScript
- **Build Tool:** Vite
- **UI Library:** Material UI
- **Testing:** React Testing Library

### Infrastructure
- **CI/CD:** GitHub Actions
- **Container:** Docker & Docker Compose
- **Hosting:** Managed cloud platform (AWS/GCP/Azure)
- **Blockchain (Optional):** EVM-compatible network (Sepolia for testing)

## 📁 Repository Structure

```
verifiable-records-saas/
├── docs/
│   ├── 01_ARCHITECTURE.md           # System design & data flow
│   ├── 02_DATABASE_SCHEMA.md        # Complete DB design
│   ├── 03_API_DESIGN.md             # REST API specification
│   ├── 04_SETUP_GUIDE.md            # Local development setup
│   ├── 05_SECURITY_CHECKLIST.md     # Security analysis & checklist
│   ├── 06_DEPLOYMENT_GUIDE.md       # Production deployment
│   ├── 07_BLOCKCHAIN_OPTIONAL.md    # Blockchain integration (phase 2)
│   ├── CUSTOMER_VALIDATION.md       # Market validation approach
│   ├── BUSINESS_MODEL.md            # Pricing & revenue strategy
│   └── CONTRIBUTING.md              # Dev guidelines
├── apps/
│   ├── api/                         # Spring Boot backend
│   │   ├── src/main/java/
│   │   ├── src/test/java/
│   │   └── pom.xml
│   └── web/                         # React frontend
│       ├── src/
│       ├── public/
│       └── package.json
├── infrastructure/
│   ├── docker/
│   │   ├── Dockerfile.api
│   │   └── Dockerfile.web
│   └── deployment/
│       ├── docker-compose.yml
│       └── .env.example
├── .github/
│   └── workflows/
│       ├── test.yml
│       ├── security-scan.yml
│       └── deploy.yml
└── README.md
```

## 🚀 Quick Start

### Prerequisites
- Java 17 or higher
- Node.js 18 or higher
- Docker & Docker Compose
- Git

### Local Development

1. **Clone the repository:**
   ```bash
   git clone https://github.com/tejasvimys/verifiable-records-saas.git
   cd verifiable-records-saas
   ```

2. **Start local environment:**
   ```bash
   docker-compose up -d
   ```

3. **Setup backend:**
   ```bash
   cd apps/api
   ./mvnw clean install
   ./mvnw spring-boot:run
   ```

4. **Setup frontend:**
   ```bash
   cd apps/web
   npm install
   npm run dev
   ```

5. **Access the application:**
   - Frontend: http://localhost:5173
   - API Docs: http://localhost:8080/swagger-ui.html
   - Database: localhost:5432 (postgres/password)

For detailed setup instructions, see [SETUP_GUIDE.md](docs/04_SETUP_GUIDE.md).

## 📚 Documentation Reading Order

Start with these docs in this order:

1. **[01_ARCHITECTURE.md](docs/01_ARCHITECTURE.md)** - Understand the system design and how components interact
2. **[02_DATABASE_SCHEMA.md](docs/02_DATABASE_SCHEMA.md)** - Learn the data model and table relationships
3. **[03_API_DESIGN.md](docs/03_API_DESIGN.md)** - API endpoints, request/response formats, and contracts
4. **[04_SETUP_GUIDE.md](docs/04_SETUP_GUIDE.md)** - Get your local environment running
5. **[05_SECURITY_CHECKLIST.md](docs/05_SECURITY_CHECKLIST.md)** - Pre-launch security review and testing
6. **[06_DEPLOYMENT_GUIDE.md](docs/06_DEPLOYMENT_GUIDE.md)** - Production deployment instructions
7. **[07_BLOCKCHAIN_OPTIONAL.md](docs/07_BLOCKCHAIN_OPTIONAL.md)** - Phase 2 blockchain integration (after customer validation)
8. **[CUSTOMER_VALIDATION.md](docs/CUSTOMER_VALIDATION.md)** - Market research and pilot strategy
9. **[BUSINESS_MODEL.md](docs/BUSINESS_MODEL.md)** - Pricing and revenue strategy

## 💰 Business Model

### Pricing Strategy (Test Prices)
- **Paid Pilot:** $300–$500 (credited toward onboarding)
- **Standard Onboarding:** $500–$1,500
- **Starter Plan:** $99/month (up to 1,000 credentials/month)
- **Business Plan:** $249/month (up to 10,000 credentials/month)
- **API/Enterprise:** $499+/month (unlimited, custom integrations)

### Target Customers (Priority Order)
1. **Training & Certification Providers** (first pilots)
2. **Small Manufacturers/Distributors** (phase 2)
3. **Nonprofits/Religious Organizations** (phase 3)

## 🔒 Security First

- ✅ Tenant isolation enforced on every API call
- ✅ Digital signatures with Ed25519 or industry standards
- ✅ Private keys stored in protected signing environment
- ✅ Rate limiting and API key scoping
- ✅ Audit trail for all security-relevant actions
- ✅ Independent security review before production

## 📋 Launch Acceptance Criteria

Before going live, all of these must pass:

- ✅ Organization can invite users and issue credentials
- ✅ Third parties can verify signatures without logging in
- ✅ Changing payload causes verification to fail
- ✅ Revoked and expired credentials are properly distinguished
- ✅ Tenant isolation tests pass for read, update, revoke, export
- ✅ Signing and API keys can be rotated/revoked
- ✅ Blockchain transaction failure doesn't invalidate credentials
- ✅ Audit events recorded for security-relevant actions
- ✅ Backups can be restored successfully
- ✅ At least 1 customer paid and tested the workflow

## 🤝 Contributing

See [CONTRIBUTING.md](docs/CONTRIBUTING.md) for:
- Code style guidelines
- PR workflow
- Testing requirements
- Commit message conventions

## 📄 License

MIT License

---

**Status:** Pre-launch MVP  
**Last Updated:** October 27, 2024  
**Maintainers:** @tejasvimys
