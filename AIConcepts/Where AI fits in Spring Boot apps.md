# Where AI fits in Spring Boot
“In Spring Boot applications, AI typically sits in the service layer as an external dependency, providing decision support or text processing, while the application enforces validation, security, and business rules.”

~~~
Controller
   ↓
Service  ←── AI integration happens here
   ↓
Repository / External APIs (LLM)
~~~

> [!Tip]
>
> “AI calls belong in the service layer, not the controller.”

## Common Ways Spring Boot Uses AI (MOST IMPORTANT)
### 1. AI as a Decision Support Component

AI assists, it doesn’t decide.

**Examples:**
- Summarize logs
- Explain errors
- Classify tickets
- Suggest next actions

**Spring Boot Role:**
- Sends data to AI
- Gets suggestions
- Applies business rules

> [!Tip]
>
> Interview line:
> 
> “AI augments decisions; business logic remains deterministic.”

### 2. AI as a Text Processing Engine

**Examples:**
- Text summarization
- Entity extraction
- Translation
- Sentiment analysis

**Spring Boot Role:**
- Pre-process input
- Call AI
- Post-process output

### 3. AI as a Search / Q&A Layer (RAG)

Used when AI must answer based on your data.

**Flow:**
~~~
User question
 → Spring Boot
 → Fetch relevant docs
 → Send docs + question to AI
 → Answer
~~~

> [!Tip]
>
> Important to say:
> 
> “We don’t rely on model memory; we ground answers using retrieved data.”

### 4. AI behind a Controlled API / Feature

**AI is wrapped inside:**
- Feature flags
- Rate limits
- Validation
- Audit logs

**Spring Boot ensures:**
- Safety
- Observability
- Cost control

## What Spring Boot is Responsible For

### Spring Boot handles:
- Prompt construction
- Context selection
- Validation of AI output
- Retries & timeouts
- Rate limiting
- Security & masking
- Auditing & logging

### Spring Boot does NOT:
- Train models
- Tune weights
- Decide truth
- Replace business logic

## How AI fits into Microservices (important)
Two patterns you should know:

**Pattern 1:** AI inside an existing service

~~~
Order Service → calls AI for summary
~~~

✔ Simple
✔ Fast to build
✔ Good for small features

**Pattern 2:** Dedicated AI microservice (preferred)

~~~
Any Service → AI-Helper Service → LLM
~~~

✔ Centralized prompts
✔ Easier governance
✔ Reusable across teams

> [!Tip]
> 
> Interview line:
>
> “For larger systems, we isolate AI usage into a dedicated service.”
