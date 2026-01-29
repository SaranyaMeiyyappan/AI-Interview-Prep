## Statelessness
### General Concept
A state where the AI does not remember previous interactions after a response is given.

### Interview Addon
**LLMs are stateless by default**, meaning they do not retain memory of previous interactions once a response is generated.

Any conversational memory or long-term context must be explicitly provided by the application on each request.
“Statelessness **improves security** because sensitive data is not implicitly retained by the model across requests.”

> [!Tip]
>
> **Advanced agents**
>
> In cases while moving from stateless to **stateful**, the application owns the state — not the model — which allows us to apply access control, encryption, and auditing.”
>
> That aligns with Spring Boot + enterprise security thinking.

> [!Note]
>
> Q: How do you maintain conversation context then?
> 
> A: “The backend explicitly re-sends relevant context from a database or cache with each request. The model itself remains stateless.”

## Security Considerations

### Prompt Injection

Manipulating the model with crafted input that forces it to override or manipulate system instructions. This risk can be amplified by higher temperature settings.

### Agentic Vulnerabilities

When LLMs are integrated with tools or actions, responses must be treated as untrusted input and strictly validated before execution.

### Context & RAG Security
Since retrieved documents influence model output, access control on vector stores is as important as securing the primary database.

>[!Tip]
>
> **Golden Rule**
>“LLM output should be treated like user input — never trusted blindly.”
