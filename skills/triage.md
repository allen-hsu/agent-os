# Skill: Triage

## Purpose
Classify an incoming request and decide how to handle it.

## Steps
1. Parse the request — what is the human asking for?
2. Classify by domain: code / writing / research / operations / meta / simple
3. Check complexity: can I handle this directly?
4. Route:
   - Single-domain, clear scope → delegate to specialist
   - Multi-domain → break into sub-tasks, delegate each, synthesize
   - Ambiguous → ask human for clarification
   - Meta (about AgentOS itself) → handle directly

## Output
A routing decision: handle directly, delegate to specific agent, or ask for clarification.
