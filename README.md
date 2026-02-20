# Jan-Suraksha: A National Pharmacogenomic Safety Infrastructure

### **Project Overview**

**Jan-Suraksha** (PharmaGuard) is a regulated Clinical Decision Support System (CDSS) engineered by **Team Vistara** for the RIFT 2026 Hackathon. Unlike traditional "black-box" AI tools, Jan-Suraksha is built as a **Deterministic Safety Kernel** designed to eliminate adverse drug reactions (ADRs) within the Indian healthcare ecosystem.

By decoupling high-stakes clinical logic from narrative AI, we provide a system that is 100% compliant with **CPIC Level A guidelines** and ready for integration with the **Ayushman Bharat Digital Mission (ABDM)**.

---

### **🔗 Critical Links**

Live Deployed Application: [https://rift-team-vistara.netlify.app/ ](https://ai.studio/apps/df0eb50b-b007-4bef-8fb6-cf80605b7cbc)
LinkedIn Video Demo:https://www.linkedin.com/posts/krishna-gupta-b53758389_rift2026-pharmaguard-pharmacogenomics-ugcPost-7430438314882650112-fDz5?utm_source=share&utm_medium=member_desktop&rcm=ACoAAF-vdW8B6gqomy2RJi6tPyYQ6GdaSj3Jj4M

---

### **1️⃣ Problem Statement: The Specialist Gap in India**

In India, medication is often a "one-size-fits-all" experiment. However, genetic diversity across 4,000+ ethnic groups means standard doses fail **30% of the time**.

* **Clinical Toll:** ADRs account for up to **7.9% of hospital admissions** in India.
* **The Burden:** Up to **35% of Indian cardiac patients** carry  mutations, rendering blood thinners like Clopidogrel ineffective.
* **Infrastructure Gap:** Tier-2 and Tier-3 hospitals lack the on-site geneticists required to interpret 20-page genomic reports. Doctors need actionable safety labels in **under 10 seconds**.

---

### **2️⃣ The Innovation: Deterministic Clinical Kernel**

Jan-Suraksha’s primary differentiation is its **"Separation of Concerns"** architecture:

* **Layer 1: Deterministic Core (Hard Logic):** A non-AI mathematical engine that maps genotypes to phenotypes using an absolute Activity Scoring system. For example, the activity score () for  is calculated as the sum of functional values assigned to each allele:



Phenotypes are assigned strictly based on these scores (, , , ).
* **Layer 2: Controlled Narrative Layer (LLM):** An LLM acting only as a "Translator." It takes pre-computed hard facts and verbalizes a 3-sentence explanation. The AI is physically barred from modifying risk labels or dosages, ensuring **zero hallucinations**.

---

### **3️⃣ Key Features & Differentiation**

* **Automated Phenoconversion:** The algorithm adjusts a patient's status in real-time based on **Drug-Drug-Gene Interactions (DDGI)**. A "Normal Metabolizer" taking a CYP2D6 inhibitor is automatically re-flagged as a **Poor Metabolizer**.


* **Indian Allele Moat:** Pre-loaded with **South Asian (SAS) allele frequencies** from the IndiGen initiative to ensure accuracy for the Indian population.
* **ABDM-Native Infrastructure:** Seamless integration with **ABHA IDs** and the national Consent Manager framework for longitudinal, portable safety profiles.
* **CDSCO Class C Readiness:** Engineered as a **Software as a Medical Device (SaMD)** with a built-in Algorithm Change Protocol (ACP) for Indian regulation.

---

### **4️⃣ Tech Stack & Architecture**

* **Frontend:** React + TypeScript (Tailwind CSS) for an accessibility-first (WCAG 2.2 AAA) clinical HUD.
* **Backend:** **FastAPI** with **cyvcf2** for high-performance parsing of **VCF v4.2** files.


* **Processing:** **Celery + Redis** task queues for asynchronous genomic normalization against the **GRCh38** reference.
* **Explainability:** **MEGA-RAG** framework utilizing vector embeddings of CPIC guidelines to ground LLM responses in verifiable truth.
* **Orchestration:** **Model Context Protocol (MCP)** to securely bridge the AI narrator with external repositories without exposing PHI.



---

### **5️⃣ Installation & Setup**

**Prerequisites:**

* Python 3.10+
* Node.js 18+
* Redis (for task queuing)

**Backend Setup:**

```bash
cd backend
pip install -r requirements.txt
cp.env.example.env # Add your OpenAI API key
python main.py

```

**Frontend Setup:**

```bash
cd frontend
npm install
npm run dev

```

---

### **6️⃣ API Documentation & Schema Compliance**

Our system guarantees 100% adherence to the mandated JSON schema.

**Example Output:**

```json
{
  "patient_id": "PATIENT VISTARA-001",
  "drug": "CODEINE",
  "risk_assessment": {
    "risk_label": "Toxic",
    "confidence_score": 1.0,
    "severity": "high"
  },
  "pharmacogenomic_profile": {
    "primary_gene": "CYP2D6",
    "diplotype": "*4/*4",
    "phenotype": "PM"
  },
  "llm_generated_explanation": {
    "summary": "Patient is a CYP2D6 Poor Metabolizer. Codeine cannot be converted to its active form (morphine), leading to therapeutic failure and risk of adverse effects."
  },
  "quality_metrics": {
    "vcf_parsing_success": true
  }
}

```

---

### **7️⃣ Team Vistara**

**Institution:** PW Institute of Innovation (PW IOI)

* **Krishna Gupta:** Lead Developer 
* **Dhruvraj Nikkam:** Systems Architect 

---

### **8️⃣ Acknowledgements**

Built for the **PharmaGuard HealthTech Track** at RIFT 2026. Data anchored to **CPIC Level A guidelines** and the **PharmGKB** knowledge base.

*Jan-Suraksha: Precision Medicine for Every Indian Citizen.*
