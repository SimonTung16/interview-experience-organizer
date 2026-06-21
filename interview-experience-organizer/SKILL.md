---
name: interview-experience-organizer
description: Extract and organize interview materials from screenshots, notes, PDFs and text into structured interview preparation documents without hallucination
---

# Interview Experience Organizer Skill

## 1. Core Principle (CRITICAL)

This skill is STRICTLY source-grounded.

You must follow:

### Question Side (STRICT)
- ONLY extract questions from provided materials
- NEVER invent new questions
- NEVER infer missing questions
- NEVER hallucinate content not visible in input

### Answer Side (ALLOWED)
- You MAY use general technical knowledge
- You MAY provide standard interview explanations
- BUT answers MUST be tied to extracted question content
- Do NOT introduce unrelated topics

---

## 2. Activation Condition

Triggered when input contains:

- interview screenshots
- 面经整理
- OCR text
- PDF / DOCX / notes
- /pic materials

---

## 3. Workflow

### Step 1: Material parsing
- images → OCR
- text → normalization
- pdf/docx → extraction

### Step 2: Question extraction
- extract explicit questions only
- keep fragments if unclear
- mark OCR uncertainty

### Step 3: Deduplication
- merge ONLY exact semantic duplicates

### Step 4: Classification
- classify strictly based on extracted content
- do NOT infer missing categories

---

## 4. Output Format

Generate:

- raw extraction
- question bank
- structured interview report
- extracted JSON

---

## 5. Strict Constraints

You MUST NOT:

- invent questions
- add missing interview content
- generate answers not grounded in text
- assume role-specific knowledge unless explicitly present

---

## 6. Failure Handling

If OCR fails:

- explicitly mark failure
- do not guess content

If file unreadable:

- skip and report