# Exno.3-Scenario-Based Report Development Utilizing Diverse Prompting Techniques
### DATE: 10/09/2025                                                                           
### REGISTER NUMBER: 212223060291
### Aim: To design an AI-powered chatbot that assists customers in resolving issues related to product troubleshooting, order tracking, and general inquiries. The chatbot should handle various customer queries efficiently while maintaining a conversational and user-friendly tone. This experiment demonstrates different prompt engineering techniques — Straightforward Prompts, Tabular Format Prompting, Missing-Word (cloze) Prompting, and Preceding Question Prompting — and shows example prompts + expected behavior for each.

### Algorithm: 
```
1. Straightforward Prompts
Objective: Give the model a clear, explicit instruction for common tasks (short, deterministic responses).
Prompt pattern (example):
Prompt: "When a customer asks for the status of their order, reply with: 
'Your order is currently being processed and will be delivered by [date].'
If a tracking number is available, include: 'Tracking: [tracking_number]'."

Example input → expected bot output:
Customer: "What's the status of order #12345?"
Bot: "Your order is currently being processed and will be delivered by June 15, 2025. Tracking: TRK12345."

2. Tabular Format Prompting
Objective: Provide structured data or options using a compact table that the model uses to produce consistent outputs. Useful for mapping issue types → troubleshooting steps or escalation levels.
Prompt pattern (table included inside prompt):
Prompt: "Use the following table to reply to customers. Match Issue Type to Steps and Tone.

| Issue Type         | Steps (brief)                                   | Tone       |
|--------------------|-------------------------------------------------|------------|
| Order Tracking     | Check status → Provide ETA → Give tracking link | Reassuring |
| Product Troubleshoot| Basic checks → Reproduce → Next steps/escalate | Helpful    |
| Returns/Refunds    | Policy summary → Steps to return → Refund time  | Empathetic |

When user asks, identify Issue Type and respond with Steps in the listed Tone."
Example input → expected bot output:
Customer: "My package is late."
Bot: "I’m sorry your package hasn’t arrived. I’ve checked your order — it’s delayed in transit and should arrive by June 17, 2025. Here’s your tracking link: [link]. I’ll keep an eye on it for you."

3. Missing-Word (Cloze) Prompting
Objective: Give the model a partially completed template with blanks to fill, guaranteeing consistency and making the model complete key variables. Good for reply templates and automated fields.
Prompt pattern (example):
Prompt: "Fill in the blanks in this reply template using information from the customer's message:
'Hello [name], thanks for contacting us. Your order [order_id] is currently [status]. Expected delivery: [date]. If you need anything else, reply with [option].'"
Customer message: "Hi, I'm Anya. Order 98765 hasn't arrived."

Expected bot output:
"Hello Anya, thanks for contacting us. Your order 98765 is currently delayed in transit. Expected delivery: June 17, 2025. If you need anything else, reply with 'help'."

4. Preceding Question Prompting
Objective: Force the chatbot to confirm ambiguous requests by asking a short clarifying or preceding question before taking action. Useful to avoid mistaken escalations or wrong-account lookups.
Prompt pattern (example):
Prompt: "If the customer's request lacks a required identifier (order id, product model, or account email), first ask a single clarifying question. Example:
Customer: 'My order hasn't arrived.'
Bot: 'Are you referring to order number or a subscription delivery? Please provide your order number or email so I can check.'"
Example flow:
Customer: "I want a refund."
Bot: "I can help with that — could you please share your order number or the email used to place the order?"

5. (Included earlier in your supplied list) Few-Shot Prompting
Objective: Teach the model by example. Provide 2–4 example Q→A pairs and then ask it to respond to a new, similar query.
Example in-prompt: include 3 example troubleshooting Q→A lines, then new question.

6. Chain-of-Thought / Step-by-Step Prompting
Objective: For complex technical issues, instruct the chatbot to list diagnostic steps and ask the customer to confirm after each. This produces safer, more accurate troubleshooting.
Example: For overheating laptops — list checks (surface, vents, resource usage), ask customer to try each and report back.

7. Instruction with Constraints
Objective: Enforce constraints like max words, tone, or forbidden jargon.
Prompt snippet: "Respond to order inquiries in ≤ 50 words, conversational tone, no technical jargon."

8. Reflective Prompting
Objective: Reduce misunderstanding by reflecting the user's issue before replying.
Example: Customer: "How do I reset my password?"
Bot: "You're asking how to reset your password, right? Here's how…"
```
```
Example Prompts & Sample Conversations (Combined Techniques)
1. Straightforward + Missing-Word
Prompt: provide a template reply for "order delivered" and instruct model to fill [date] and [name].
Conversation:
User: "Order 4321 arrived — how do I return it?"
Bot: "Hi! You're requesting a return for order 4321. To start a return, please confirm: reason for return and whether the item is unopened."

2. Tabular + Preceding Question
Model uses table to classify issue, but if classification confidence low (ambiguous), it asks a preceding clarifying question.

3. Chain-of-Thought + Few-Shot
Provide step-by-step diagnostic examples for three device problems, then ask the model to handle "My app keeps crashing" and produce steps.
```





## Result:
The various types of Prompts are executed successfully.
