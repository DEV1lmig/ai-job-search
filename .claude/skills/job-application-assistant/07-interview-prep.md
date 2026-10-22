---
framework_version: 1.0.0
---

# Interview Preparation Guide

<!-- STAR examples drafted from public project info on 2026-10-22; fill the VERIFY notes with real numbers -->

## STAR Format

Structure answers as: **Situation** (context), **Task** (your responsibility), **Action** (what you did), **Result** (outcome).

Keep answers to 1-2 minutes. Be specific. End with what you learned or would do differently.

## Ready-Made STAR Examples

<!-- Drafted 2026-10-22 from public project descriptions (portfolio + GitHub README). The S/T/A are grounded
in what the projects say; the R lines need your real numbers. Fill in the VERIFY notes before an interview. -->

### 1. data2bids document pipeline (Backend / AI engineering, system design)
**S:** Construction bid teams keep plans, drawings, spreadsheets and photos spread across Google Drive folders and cannot get answers out of them quickly.
**T:** Build the pipeline that turns those files into something an AI can answer questions over, with answers that cite the source file and page.
**A:** Built a read-only Google Drive sync (folders stay where they are), then a queue-driven worker on Kubernetes (Azure AKS + Service Bus) that runs OCR, chunking, embeddings and GraphRAG. Scoped every query to one company for tenant isolation. Python/FastAPI API, React + TanStack Router frontend.
**R:** Product in production at https://www.data2bids.com; 1,400+ commits across API, frontend and pipeline. <!-- VERIFY: add document volume, latency, customer count -->
**Use for:** "Tell me about a complex system you built", "How do you design for reliability / scale?", "Describe your RAG experience"

### 2. MCP server for Claude and ChatGPT (Integration / API design)
**S:** Users wanted to ask questions about a bid from the assistant they already use instead of a separate chat UI.
**T:** Expose data2bids projects to Claude and ChatGPT securely.
**A:** Built a custom MCP (Model Context Protocol) server with OAuth so both assistants can query a project; kept the same per-company scoping and cited-answer guarantees as the web app.
**R:** Both assistants can answer bid questions over OAuth; one integration surface instead of two. <!-- VERIFY: usage numbers -->
**Use for:** "Tell me about an integration you designed", "How do you handle auth between services?", "Experience with LLM tooling"

### 3. Playchive: one backend for web and mobile (Product ownership / full-stack)
**S:** Wanted a home for a gaming life: backlog, now-playing tracking, reviews, with both a web and a mobile app.
**T:** Own product, design and development solo, and avoid building two backends.
**A:** Next.js + React + Tailwind web app and an Expo mobile app sharing a single Convex backend; Clerk for auth; IGDB for the game catalog. Designed the brand board and a 3D shelf landing page.
**R:** Live at https://playchive.vercel.app; one backend, two clients. <!-- VERIFY: users, signups -->
**Use for:** "Tell me about a side project", "How do you make architecture decisions?", "Show me something you own end to end"

### 4. Pycher thesis: AI-adapted Python learning (Delivery under a deadline / applied AI)
**S:** Thesis project at URBE: learners get the same static Python material regardless of level.
**T:** Build an interactive platform that adapts Python learning materials with AI and validates exercises.
**A:** React + Vite frontend, FastAPI backend with SQLAlchemy/Alembic on PostgreSQL, Redis, Docker Compose; wrote tests for exercise input validation and type checking.
**R:** Thesis delivered and defended; repo public at https://github.com/DEV1lmig/pycher. <!-- VERIFY: grade, pilot users -->
**Use for:** "Tell me about a project with a hard deadline", "How do you test?", "Academic project you are proud of"

### 5. Freelance design process (Communication / client management)
**S:** Freelance UI/UX clients since 2020 with changing requirements and no shared process.
**T:** Deliver on time and keep clients informed.
**A:** Set clear milestones up front, keep a written log of every change, update the client weekly by meeting or email.
**R:** Repeat freelance work since 2020 and a reusable process now applied to engineering work. <!-- VERIFY: a concrete client outcome -->
**Use for:** "How do you handle deadlines?", "How do you communicate with stakeholders?", "Tell me about handling scope changes"

<!-- Add more STAR examples as needed. Aim for 4-6 covering different competencies. -->

## Common Tough Questions

### "Why are you looking to leave data2bids / your current role?"
> Draft: "I built most of data2bids from the API to the pipeline and it is in production. I want the next step: a bigger engineering team to learn from, and a product where the AI-over-documents work I have done is the core, not one feature." <!-- VERIFY: your real reason -->

### "You don't have [team leadership / enterprise / ML research] experience."
> Draft: "Correct, my experience is as the engineer who owns the full stack. What I bring is a production RAG pipeline, an MCP integration shipped to real users and a written, milestone-driven process. I am looking for a team where I can grow into [the gap]."

### "Where do you see yourself in 5 years?"
> Draft: "Leading the technical side of an AI product: owning architecture decisions for document or agent pipelines and mentoring engineers who join after me." <!-- VERIFY -->

### "What's your biggest weakness?"
> Draft: "I default to building things myself. I mitigate it by writing the spec and change log first so others can pick up the work, and by asking for review before merging." <!-- VERIFY -->

### "Why this company specifically?"
> Customize per company. Must reference: specific projects, company values, market position, or team structure. Never give a generic answer.

## Questions You Should Ask Interviewers

### About the Role
- "What does a typical week look like in this role?"
- "What would success look like in the first 6 months?"
- "What's the biggest challenge the team is facing right now?"

### About the Team
- "How big is the team, and how do you divide work?"
- "What does the development/project lifecycle look like, from idea to production?"
- "How do you onboard new team members?"

### About Tech & Growth
- "What's your current tech stack for [relevant area]?"
- "Is there room to grow into more architectural or strategic decisions?"
- "How does the team stay current with new tools and methods?"

### About Culture (use these to prevent disappointment)
- "How would you describe the team culture?"
- "What does professional development look like here?"
- "Is there flexibility for remote/hybrid work?"
- "What's the balance between development/new projects and maintenance work?"
- "How would you describe the leadership style in this team?"
- "What do people who thrive here have in common?"

## Phone/Video Interview Tips
- Have STAR examples written out (use this file)
- Keep a glass of water nearby
- Smile when speaking (it changes your tone)
- Ask for clarification if a question is vague
- It's OK to take 5 seconds to think before answering
- End with: "Is there anything else you'd like to know about my background?"

## After the Application (Best Practice)

### Follow-Up Etiquette
- **Don't call to "stand out"** or to learn more about the role post-submission - this risks a negative impression
- If the employer specified a timeline, respect it and wait
- If no timeline was given and significant time has passed (2+ weeks), a brief call to ask about status is acceptable
- If you have genuinely new, relevant information to share, a short follow-up is fine

### Thank-You Notes
- When you receive any update (interview invitation, rejection, or status update), send a brief thank-you message
- Express appreciation for their time and the process
- Keep it short (2-3 sentences)

## Roleplay Guidelines
When the user asks for interview practice:
1. Ask which role/company to simulate
2. Start with easy warm-up questions ("Tell me about yourself")
3. Progress to role-specific technical questions
4. Include 1-2 behavioral questions using the competencies from the job posting
5. End with a tough question or curveball
6. After each answer, give brief feedback: what worked, what to sharpen
7. Suggest which STAR example would work best for each question
