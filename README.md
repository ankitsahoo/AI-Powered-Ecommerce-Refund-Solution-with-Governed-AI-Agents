# AI-Powered-Ecommerce-Refund-Solution-with-Governed-AI-Agents

A real e-commerce return/refund process, run by a governed multi-agent AI system. Most "AI agent" demos are a chatbot with a nice prompt. ReturnGuard is the opposite: one company, one real operational process — reviewing every return/refund request — handed to a system of AI agents that is watched, bounded, and reversible. The agents auto-clear the obviously-legitimate returns and route anything risky, unclear, or expensive to a human, through a real fraud-review dashboard. Every decision is traceable to the exact model, prompt version, policy version, inputs, tokens, and cost that produced it. It's a portfolio project for Forward Deployed Engineer work — the emphasis is on the parts that are hard in the field: governed autonomy, full observability, per-agent identity, scenario-driven validation, a business case, and a clean handoff — not on "an agent that answers".

**Summary**
- A real e-commerce return/refund pipeline where 10 specialized agents (data-quality, policy, image, behavior, decision, critic, etc.) jointly review each case.
- A reviewer/admin dashboard with a shadow → suggest → assist → auto automation ladder and a global kill switch.
- A fully local, Docker Compose–run stack (FastAPI, LangGraph, Bifrost, ContextForge, OPA, Langfuse, Keycloak) with an append-only, hash-chained audit log for every action.
