## Token
Token is the basic unit of text that an LLM processes. Both the prompt and the response are broken down into tokens, which may represent parts of words, punctuation, or symbols.

From a system design perspective, token usage directly affects latency, cost, and response size, so prompts must be kept concise and relevant.

> [!TIP]
> 
> Bring this point up only when discussing:
>
> - Performance
> - Cost
> - Context window limits
>
> **Example:**
> 
> “Since everything is converted into tokens internally, long prompts increase token count and directly affect latency and cost.”
> 
> “Internally, the LLM converts text into tokens, and each token is represented as a numerical value so the model can process it.”
>
> “Just like we serialize objects before sending them over the network, LLMs tokenize text and convert it into numbers before processing.”
> 
> **Mental model (keep this)**
> 
> Text → Tokenization → Numeric Representation → Model Processing → Tokens → Text

## Context
Context refers to all the information the model can see during a single request — including system instructions, user prompt, conversation history, and any retrieved documents.

Since the model has a limited context window, applications must carefully manage what information is included to avoid losing important instructions.

> [!Important]
> “In a Spring Boot application, context is explicitly assembled by the service layer — the model does not remember previous requests unless we send the data again.”
>
> This shows:
>
> - Stateless thinking
> - HTTP alignment
> - Backend maturity
>
> **Practical analogy (very effective in interviews)**
> “The context window is like a method stack frame — once it overflows or irrelevant data is added, important variables get lost.”

> [!Note]
> 
> Q: What happens if the context is too large?
> 
> A: “The model may ignore earlier instructions, responses become slower and more expensive, and output quality degrades.”
