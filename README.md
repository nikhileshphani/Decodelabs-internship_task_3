# 🧠 Task 3: The Knowledge Analyst — RAG Legal Document Intelligence System

> **DecodeLabs Generative AI Internship   
> Simulating Retrieval-Augmented Generation (RAG) for Legal Document Analysis

---

## 📌 Project Summary

This project simulates a **Retrieval-Augmented Generation (RAG)** pipeline applied to a real legal document — the Nebraska Supreme Court case *American Exchange Bank v. Topp (2026)*. The AI model is constrained through careful prompt engineering to extract structured information **only from the source document**, citing specific page numbers for every fact.

The goal: prove that an AI can act as a legal analyst that never hallucinates, always cites its sources, and delivers structured output ready for use in a real legal brief.

---

## 🎯 Task Requirements 

| Requirement | Status |
|---|---|
| Feed a long legal document into an AI model | ✅ Done |
| Engineer prompts that force the AI to cite specific page numbers/sections | ✅ Done |
| Create a Summary Dashboard extracting Risks, Dates, and Stakeholders | ✅ Done |
| Prevent hallucination (making up facts) | ✅ Done |

---

## 📂 Repository Structure

```
task-3-rag-knowledge-analyst/
│
├── prompts/
│   ├── system_prompt.png          # System prompt screenshot (RAG persona + citation rules)
│   └── user_prompt.png            # User prompt screenshot (extraction task)
│
├── source_document/
│   └── legal_ad_ex_2.pdf          # Source legal document (American Exchange Bank v. Topp)
│
├── output/
│   └── American_Exchange_Bank_v_Topp_Legal_Analysis.docx   # AI-generated summary dashboard
│
├── docs/
│   └── Task3_RAG_Project_Documentation.docx   # Full project documentation
│
└── README.md                      # This file
```

---

## 🔧 How It Works

### Layer 1 — System Prompt (Persona & Rules)

The system prompt establishes:
- **Persona**: Expert Legal Document Analyst performing RAG
- **Citation rule**: Every answer must end with `[Page X]` or `[Section Y]` reference
- **Hallucination guard**: "NEVER make up facts not present in the document"
- **Fallback**: If information not found, say so explicitly
- **Few-shot example**: Shows the exact Q&A + citation format expected

### Layer 2 — User Prompt (Extraction Task)

The user prompt instructs the AI to generate **three structured tables**:

| Table | What It Extracts |
|---|---|
| TABLE 1: RISKS & LIABILITIES | Financial risks, legal liabilities, adverse findings |
| TABLE 2: KEY DATES & DEADLINES | Important dates, timelines, deadlines |
| TABLE 3: STAKEHOLDERS & PARTIES | All named parties, judges, attorneys |

Every single row in every table **must include a source citation**.

---

## 📄 Source Document

**Case**: *American Exchange Bank v. Topp*  
**Citation**: 321 Nebraska Reports 409  
**Case No.**: S-25-290  
**Decided**: May 15, 2026  
**Court**: Nebraska Supreme Court  

**Key Legal Issues**:
- Applicability of antideficiency statutes (Neb. Rev. Stat. § 76-1013) to guarantors
- Enforceability of waiver provisions in trust deed transactions
- Whether summary judgment was proper given disputed fair market values

---

## 📊 Output Highlights

### Sample — Risks & Liabilities

| Risk Item | Details | Source |
|---|---|---|
| Capital Deficiency Claim | AEB sought $3,051,200.27 plus daily interest | Page 412, Background |
| Guarantor Personal Liability | Topps executed 4 guaranties; total principal $4,715,150 | Page 411, Background |
| Unenforceable Waiver Provision | Guaranties attempted to eliminate fair market value defense | Page 413; Page 410, Holding #8 |
| Violation of Public Policy | Trustee sale + avoiding antideficiency statute = public policy violation | Page 410, Holding #7 |

### Sample — Key Dates

| Date Event | Specific Date | Source |
|---|---|---|
| First Promissory Notes | 2015 | Page 411, Background |
| TMI Chapter 11 Bankruptcy | 2021 | Page 411, Background |
| Trustee Sales Conducted | November 2023 | Page 412, Background |
| Supreme Court Decision | May 15, 2026 | Page 409, Case Caption |

### Sample — Stakeholders

| Party | Role | Source |
|---|---|---|
| American Exchange Bank (AEB) | Appellee / Creditor-Lender | Page 409, Caption |
| Luke G. & Ria N. Topp | Appellants / Co-Guarantors | Page 409, Caption |
| Bergevin, J. | Majority Opinion Author | Page 410, Panel |
| Papik, J. | Dissenting Justice | Pages 423–426 |

---

## 🛠️ Prompt Engineering Techniques Used

| Technique | Application |
|---|---|
| **Persona Assignment** | AI assigned role of "expert Legal Document Analyst performing RAG" |
| **Few-Shot Prompting** | Example Q&A shown in system prompt to demonstrate citation format |
| **Constraint Injection** | 5 numbered critical rules enforce citation and prevent hallucination |
| **Format Specification** | Exact table column format defined using pipe notation |
| **Fallback Instruction** | Explicit rule: if not found, say so — no guessing allowed |
| **Context Framing** | "Treat as legal brief" increases AI precision and citation discipline |

---

## ✅ Results

| Metric | Target | Achieved |
|---|---|---|
| Rows with page citations | 100% | ✅ 100% (all 40+ rows) |
| Hallucinated facts | 0 | ✅ 0 detected |
| Tables generated | 3 | ✅ 3 + Critical Holdings bonus section |
| Dissenting opinion captured | Optional | ✅ Documented separately |
| Financial figures accuracy | Exact match | ✅ All verified against source |

---

## 🔑 Key Learnings

- **RAG is about prompt engineering as much as retrieval** — without strict citation rules, even good models hallucinate
- **System prompts are behavioral contracts** — every rule measurably changes output quality
- **Few-shot examples beat abstract instructions** for format enforcement
- **Legal documents are ideal RAG test cases** — every fact can be cross-verified
- **Pre-defined structured output formats** produce more consistent, usable results than free-form summaries

---

## 🧰 Tools Used

| Tool | Purpose |
|---|---|
| Claude Projects (Anthropic) | Primary AI model for document analysis |
| Legal Case PDF | Source document for RAG simulation |
| Microsoft Word | Final output format (.docx) |
| Prompt Engineering | Two-layer system prompt + user prompt design |

---

*DecodeLabs Generative AI Internship | Task 3: The Knowledge Analyst*
