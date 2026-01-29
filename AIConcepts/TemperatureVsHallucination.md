## Temperature 
Temperature controls the randomness in token selection, which affects how deterministic or creative the model’s responses are.

**At low temperature**, the model consistently chooses the most probable tokens, which makes responses more predictable and suitable for enterprise use cases like summarization or classification.

**At higher temperature,** the model introduces more randomness, which can be useful for creative tasks but increases the risk of incorrect or inconsistent outputs.

> [!Tip]
>
> Add this line if asked about real systems:
>
> “In backend applications, we typically keep temperature low to ensure reliability and repeatability.”
>
> That sentence alone screams production mindset.
> “Temperature is typically configured between 0 and 1, depending on the provider.”

## Hallucination
Hallucination occurs when an LLM generates responses that sound plausible but are factually incorrect or not grounded in provided data.

This typically happens due to insufficient grounding context, overly creative settings, or gaps in training data.”

Then add:
> [!Important]
> “Because of this, AI outputs should never be treated as the source of truth in backend systems.”
>
> “If LLM outputs are directly used to trigger actions without validation, hallucinations can lead to incorrect or unsafe system behavior.”

**Mitigation Options**
- Restrict creativity (low temperature)
- Ground responses with data (RAG or provided context)
- Constrain output format (structured JSON)
- Validate before execution (business rules)

> [!Tip]
>
> “Hallucinations often occur when the model lacks sufficient grounding context, which is why techniques like RAG are used.”
>
> **Follow Up**
>
> Q: Can hallucinations be fully eliminated?
> 
> A: “No. They can be reduced but not completely eliminated, so validation and guardrails are mandatory in production systems.”
