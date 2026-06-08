# 🏥 Medical History Knowledge Graph

[![Java](https://img.shields.io/badge/Java-21-orange.svg)](https://www.oracle.com/java/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.2.5-brightgreen.svg)](https://spring.io/projects/spring-boot)
[![React](https://img.shields.io/badge/React-18-blue.svg)](https://reactjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-blue.svg)](https://www.typescriptlang.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)

> *Intelligent Healthcare Data Management Platform powered by Semantic Web & AI*

A comprehensive medical history management system that leverages **Knowledge Graphs**, **Semantic Web Technologies**, and **AI** to provide healthcare professionals with actionable insights from patient data.

---

## 🌟 Overview

Medical History Knowledge Graph (MHKG) is an enterprise-grade healthcare platform that transforms unstructured medical documents into a structured, queryable knowledge base. By combining **RDF/OWL ontologies**, **SPARQL queries**, and **Large Language Models**, the system enables:

- **Semantic Search**: Find medical information using natural language
- **AI-Powered Insights**: Generate clinical insights and risk assessments
- **Longitudinal Patient View**: Complete medical timeline with automated event extraction
- **Clinical Decision Support**: Drug interaction checking, guideline compliance, anomaly detection
- **Interoperability**: FHIR R4 export for seamless EHR integration

---

## ✨ Key Features

### 📊 **Intelligent Dashboard**
- Real-time health score (0-100) with trend analysis
- Medication schedule with compliance tracking
- Critical health alerts with auto-generation
- Medical summary aggregation (conditions, allergies, labs)

### 🤖 **AI-Powered Analytics**
- Clinical insight generation using GPT-4/Ollama
- Pattern detection across longitudinal data
- Risk stratification and readmission prediction
- Personalized treatment recommendations

### 📈 **Medical Timeline**
- Automated event extraction from documents (OCR + NER)
- Visual timeline with 11+ event types
- Advanced filtering and search capabilities
- Manual entry support with CRUD operations

### 🔬 **Clinical Tools (28 MCP Tools)**
- Drug interaction checking (internal + external APIs)
- Lab reference range validation
- Clinical trial search (ClinicalTrials.gov)
- FDA safety alerts monitoring
- PubMed literature validation
- Medical knowledge base search

### 📄 **Document Processing**
- Multi-format support (PDF, images, text)
- OCR with Apache Tika
- Entity extraction (conditions, medications, labs, procedures)
- Document review workflow with approval/rejection

### 🔐 **Security & Compliance**
- Role-based access control (RBAC)
- JWT authentication
- Audit trail for all operations
- GDPR-ready consent management
- FHIR R4 standard compliance

---

## 🛠️ Technology Stack

### **Backend**
- **Language**: Java 21
- **Framework**: Spring Boot 3.2.5
- **Security**: Spring Security + JWT
- **Database**: H2 (auth), Apache Jena Fuseki (knowledge graph)
- **Semantic Web**: RDF, OWL, SPARQL, Apache Jena
- **AI/ML**: LangChain4j, Azure OpenAI GPT-4, Ollama
- **Interoperability**: HAPI FHIR R4 6.10.0
- **OCR**: Apache Tika, Tesseract
- **Build**: Maven

### **Frontend**
- **Framework**: React 18 + TypeScript 5
- **Build Tool**: Vite
- **State Management**: Zustand + TanStack Query
- **UI Library**: shadcn/ui + Radix UI
- **Styling**: Tailwind CSS
- **Routing**: Wouter
- **Charts**: Recharts
- **Icons**: Lucide React

### **Infrastructure**
- **Database**: Apache Jena Fuseki (TDB2)
- **Containerization**: Docker
- **AI Models**: Azure OpenAI, Ollama (local LLM support)

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                     Frontend (React + TS)                    │
│  Dashboard | Timeline | Insights | Documents | MCP Tools    │
└────────────────────────┬────────────────────────────────────┘
                         │ REST API (24 endpoints)
┌────────────────────────┴────────────────────────────────────┐
│                  Backend (Spring Boot)                       │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐   │
│  │ Document │  │ Medical  │  │   AI     │  │   MCP    │   │
│  │ Service  │  │ Services │  │ Service  │  │ Registry │   │
│  └──────────┘  └──────────┘  └──────────┘  └──────────┘   │
└────────────────────────┬────────────────────────────────────┘
                         │
         ┌───────────────┼───────────────┐
         ▼               ▼               ▼
   ┌──────────┐   ┌──────────┐   ┌──────────┐
   │  Fuseki  │   │   LLM    │   │  H2 DB   │
   │  (RDF)   │   │ Services │   │  (Auth)  │
   └──────────┘   └──────────┘   └──────────┘
```

### **Core Components**
- **Knowledge Graph**: Medical ontology with 1000+ classes and properties
- **SPARQL Engine**: Complex queries for data aggregation and reasoning
- **LLM Integration**: Hybrid approach (rule-based + AI) for clinical insights
- **MCP Protocol**: 28 specialized medical tools for external integrations
- **Document Pipeline**: OCR → NER → Ontology Mapping → Graph Storage

---

## 📊 Project Stats

- **Codebase**: ~15,000+ lines of production code
- **Backend**: ~8,000 lines (Java)
- **Frontend**: ~7,000 lines (TypeScript/React)
- **REST Endpoints**: 24+ fully functional APIs
- **MCP Tools**: 28 clinical decision support tools
- **UI Components**: 30+ reusable components
- **Test Coverage**: Smoke tests implemented

---

## 🚀 Quick Start

### Prerequisites
- Java 21+
- Node.js 18+
- Docker
- Maven

### 1. Clone Repository
```bash
git clone <repository-url>
cd mhkg
```

### 2. Start Infrastructure
```bash
# Start Fuseki (Knowledge Graph)
docker run -d --name fuseki \
  -p 3030:3030 \
  -v ./DB/databases:/fuseki \
  -e ADMIN_PASSWORD=your_password \
  stain/jena-fuseki:latest

# Create dataset
curl -X POST http://localhost:3030/$/datasets \
  -u admin:your_password \
  -d "dbName=medical-history-kg&dbType=tdb2"
```

### 3. Start Backend
```bash
cd backend
mvn spring-boot:run
```

### 4. Start Frontend
```bash
cd frontend
npm install
npm run dev
```

### 5. Access Application
- **Frontend**: http://localhost:3000
- **Backend API**: http://localhost:3001/api
- **Fuseki UI**: http://localhost:3030

### Default Credentials
See `CREDENCIAIS_LOGIN.md` for development credentials.

---

## 📸 Screenshots

*Coming soon - Screenshots of Dashboard, Timeline, and AI Insights pages*

---

## 🗺️ Roadmap

### ✅ Completed (MVP)
- [x] Document upload and processing
- [x] Knowledge graph storage
- [x] AI-powered insights
- [x] Medical timeline
- [x] Health dashboard
- [x] 28 MCP clinical tools
- [x] FHIR export
- [x] Role-based access control

### 🚧 In Progress
- [ ] Real-time collaboration
- [ ] Mobile app (React Native)
- [ ] Wearable device integration
- [ ] Advanced analytics dashboard

### 🔮 Future
- [ ] Multi-language support
- [ ] Telemedicine integration
- [ ] Clinical trial matching
- [ ] Blockchain for audit trail
- [ ] FHIR server (not just export)

---

## 🤝 Use Cases

### **For Healthcare Providers**
- Comprehensive patient view across multiple visits
- Clinical decision support with evidence-based recommendations
- Automated risk assessment and early warning systems
- Streamlined documentation with AI-powered extraction

### **For Researchers**
- Semantic search across patient cohorts
- Longitudinal data analysis
- Literature integration (PubMed)
- Clinical trial patient matching

### **For Healthcare Systems**
- Interoperability via FHIR standard
- Scalable knowledge graph architecture
- Audit trail for compliance
- Integration with existing EHR systems

---

## 📚 Documentation

- **[Development Guide](Docs/GUIA_DESENVOLVIMENTO.md)**: Setup and development workflow
- **[Security & RBAC](Docs/SECURITY_RBAC_GUIDE.md)**: Authentication and authorization
- **[Ontology Management](Docs/ONTOLOGY_MANAGEMENT_SYSTEM.md)**: Knowledge graph structure
- **[API Documentation](backend/QUICKSTART.md)**: REST API reference
- **[Frontend Guide](frontend/FRONTEND_README.md)**: UI components and pages

---

## 🏆 Key Differentiators

1. **Semantic Web Technologies**: True knowledge graph (not just a graph database)
2. **AI-Powered**: Hybrid rule-based + LLM approach for accuracy
3. **Standards-Compliant**: FHIR R4, SNOMED CT, LOINC support
4. **Extensible**: MCP protocol for easy tool integration
5. **Production-Ready**: Security, audit trail, RBAC, error handling

---

## 🧪 Testing

```bash
# Backend smoke tests
cd backend
./run-smoke-tests.ps1

# Frontend smoke tests
cd frontend
npm run test
```

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🤝 Contributing

Contributions are welcome! Please read our [Contributing Guidelines](CONTRIBUTING.md) before submitting pull requests.

---

## 👥 Team

*Medical History Knowledge Graph* is developed by a team passionate about transforming healthcare through technology.

---

## 📞 Contact

For business inquiries, partnerships, or demonstrations:
- Email: [contact information]
- Website: [website]
- LinkedIn: [linkedin profile]

---

## 🙏 Acknowledgments

Built with:
- **Apache Jena** - RDF/SPARQL engine
- **Spring Boot** - Backend framework
- **React** - Frontend library
- **shadcn/ui** - UI components
- **OpenAI** - AI capabilities

---

<div align="center">
  
**⭐ Star this repo if you find it useful! ⭐**

*Transforming Healthcare Data into Knowledge*

</div>
