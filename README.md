# AI-Powered-Ecommerce-Refund-Solution-with-Governed-AI-Agents

A real e-commerce return/refund process, run by a governed multi-agent AI system. Most "AI agent" demos are a chatbot with a nice prompt. ReturnGuard is the opposite: one company, one real operational process — reviewing every return/refund request — handed to a system of AI agents that is watched, bounded, and reversible. The agents auto-clear the obviously-legitimate returns and route anything risky, unclear, or expensive to a human, through a real fraud-review dashboard. Every decision is traceable to the exact model, prompt version, policy version, inputs, tokens, and cost that produced it. It's a portfolio project for Forward Deployed Engineer work — the emphasis is on the parts that are hard in the field: governed autonomy, full observability, per-agent identity, scenario-driven validation, a business case, and a clean handoff — not on "an agent that answers".

# ReturnGuard — Architecture in Simple Summary

**What is it?**
An AI-powered return/refund system for e-commerce that investigates customer return requests and decides whether to approve, reject, or send them to a human.

# How it works

**Customer → Website → Backend → AI Agents → Governance → Decision**

1. Customer submits a return with order details and photos.
2. Keycloak verifies who the user is and what they can access.
3. FastAPI receives the request and stores it in PostgreSQL.
4. Redis puts the request into a queue for processing.
5. LangGraph + AI Agents investigate:
            - Check data
            - Find the return policy using RAG
            - Analyze product images
            - Check customer behavior
            - Make a recommendation
            - Critic checks the AI's reasoning
            - Generate an explanation
6. Governance layer checks whether the AI is actually allowed to take that action using OPA/MCP.
7. Human review happens for sensitive/high-value/risky decisions.
8. Final decision is recorded and the customer gets the result.
9. Langfuse, Prometheus, Grafana monitor what the AI/system is doing.
10. PostgreSQL, Redis, MinIO, Vault store business data, queues/cache, evidence/images, and secrets.

**Real-life example**
Customer says:
"My ₹50,000 laptop arrived damaged."

**ReturnGuard:**
Check order → Check policy → Analyze photo → Check behavior → AI recommendation → Governance check → Human approval if required → Refund/Return

# Architecture Diagram

<img width="1222" height="1287" alt="Architecture" src="https://github.com/user-attachments/assets/2d57a50d-a3d6-47b0-8ebf-425f3978eed6" />

