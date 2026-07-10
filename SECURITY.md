# Security Notes

> Reusable security checklist for every AI/GenAI project.
> Copy this file into every new project repo.

---

## Prompt Injection Protection

- [ ] Validate and sanitize all user inputs before passing to LLM
- [ ] Use system prompt boundaries to separate instructions from user content
- [ ] Test with adversarial inputs — attempt to override system instructions
- [ ] Never trust user-provided role or instruction overrides

## Secret Handling

- [ ] No API keys, tokens, or credentials in code or git history
- [ ] All secrets stored in `.env` file (never committed)
- [ ] `.env` is in `.gitignore`
- [ ] `.env.example` provided with placeholder values only
- [ ] Use Azure Key Vault or environment variables in production

## PII and Data Privacy

- [ ] Identify what personal data the app processes
- [ ] PII is not logged in plain text
- [ ] PII is not stored unless required
- [ ] If stored, PII is encrypted at rest
- [ ] User data is not sent to external LLM APIs without consent

## Access Control

- [ ] Authentication is required before accessing the app
- [ ] Role-based access control (RBAC) implemented if needed
- [ ] Document retrieval is scoped to the user's permitted documents
- [ ] Admin functions are protected separately

## LLM Output Safety

- [ ] Outputs are validated before being displayed or acted upon
- [ ] Hallucination mitigation — responses grounded in retrieved context
- [ ] Content safety filters enabled (Azure AI Content Safety or similar)
- [ ] Agent actions with external side effects require human approval

## Dependency Security

- [ ] `requirements.txt` or `pyproject.toml` pinned to specific versions
- [ ] Dependencies scanned for known vulnerabilities (pip-audit or Dependabot)
- [ ] No unused or abandoned packages

## Audit and Logging

- [ ] All user queries logged (without PII where possible)
- [ ] LLM calls logged with timestamp, model, token count
- [ ] Agent tool calls logged with inputs and outputs
- [ ] Logs stored securely and retained per policy

## Deployment Security

- [ ] App runs with least-privilege service account
- [ ] HTTPS enforced — no plain HTTP
- [ ] CORS configured correctly — not wildcard `*` in production
- [ ] Rate limiting applied to API endpoints
- [ ] Azure Managed Identity used instead of hardcoded credentials

---

## References

- OWASP Top 10 for LLM Applications: https://owasp.org/www-project-top-10-for-large-language-model-applications/
- Microsoft Responsible AI: https://www.microsoft.com/en-us/ai/responsible-ai
- Azure AI Content Safety: https://learn.microsoft.com/en-us/azure/ai-services/content-safety/
