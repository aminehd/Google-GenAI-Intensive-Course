
# 📓 Walkthrough: [Notebook Title]

This guide helps you finish the **[Day 1 - Prompting](https://www.kaggle.com/code/markishere/day-1-prompting)** Notebook. Follow the steps below, use the provided keywords and cues, and track your time to stay on schedule.


---

## 📚 List of Concepts
1. **Core Concepts:**
   - Prompt engineering basics
   - JSON mode for structured outputs
   - Parameter tuning (temperature, Top-K, Top-P)
   - Chain-of-Thought reasoning
   - ReAct (Reason and Act) framework
2. **Tools:**
   - Python SDK
   - Gemini API
3. **Techniques:**
   - Zero-shot prompting
   - Few-shot prompting
   - Code generation and execution

---

## ✅ By the End of This Notebook
You will have:
- **Completed Setup:** Installed and configured all required dependencies and tested the API key.
- **Explored Prompts:** Experimented with zero-shot, few-shot, and reasoning-based prompts.
- **Adjusted Parameters:** Learned how to modify temperature, Top-K, and Top-P for diverse outputs.
- **Tested Reasoning Techniques:** Used Chain-of-Thought and ReAct examples.
- **Documented Learnings:** Recorded key takeaways, insights, and troubleshooting steps.

---


---

## ⏱️ Time Breakdown

| Task                          | Description                                    | Estimated Time |
|-------------------------------|------------------------------------------------|----------------|
| **Setup**                     | Install dependencies, set up API key           | 10-15 minutes  |
| **Run First Prompt**           | Test API key with a basic prompt              | 5-10 minutes   |
| **Explore Zero-shot Prompts**  | Run examples, modify text, analyze outputs    | 20-30 minutes  |
| **Experiment with Parameters** | Adjust temperature, Top-K, Top-P values       | 30-45 minutes  |
| **Chain-of-Thought Example**   | Test reasoning with intermediate steps        | 30 minutes     |

---

Summary of code
Here’s a very short summary of what the code in the notebook does:

1. **Setup:** Installs and configures the Gemini API with an API key.
2. **First Prompt:** Tests if the setup works by generating a simple AI response.
3. **Zero-shot Prompting:** Classifies or generates text without prior examples.
4. **Parameter Tuning:** Adjusts `temperature`, `Top-K`, and `Top-P` to control output randomness and diversity.
When both are supplied, the Gemini API will filter top-K tokens first, then top-P and then finally sample from the candidate tokens using the supplied temperature.

5. **Chain-of-Thought Reasoning:** Generates intermediate reasoning steps for complex problems.
6. **ReAct Framework:** Combines reasoning, actions, and observations for question-answering tasks.
7. **Code Generation:** Uses the API to create Python code or structured JSON outputs.

Code snippets for core functionalities:

1. **Setup:**
   ```python
   import google.generativeai as genai

   genai.configure(api_key="YOUR_API_KEY")
   flash = genai.GenerativeModel('gemini-1.5-flash')

   ```

2. **First Prompt:**
   ```python
   flash.generate_content("Explain AI to me like I'm a kid.")
   ```

3. **Zero-shot Prompting:**
   ```python
   flash.generate_content("Classify this review: 'Great movie!'")
   ```

4. **Parameter Tuning:**
   ```python
   genai.GenerationConfig(temperature=0.7, top_k=40, top_p=0.9)
   ```

5. **Chain-of-Thought:**
   ```python
   flash.generate_content("How old is my partner? Let's think step by step.")
   ```

6. **ReAct Framework:**
   ```python
   "<search>Transformers NLP paper</search>"
   ```

7. **Code Generation:**
   ```python
   flash.generate_content("Write a Python function to calculate factorial.")
   ``` 
8. **Retry:** 
    ```python
    from google.api_core import retry

    high_temp_model = genai.GenerativeModel(
        'gemini-1.5-flash',
        generation_config=genai.GenerationConfig(temperature=2.0))


    # When running lots of queries, it's a good practice to use a retry policy so your code
    # automatically retries when hitting Resource Exhausted (quota limit) errors.
    retry_policy = {
        "retry": retry.Retry(predicate=retry.if_transient_error, initial=10, multiplier=1.5, timeout=300)
    }
    ```
  9. **Response mime type:**
     ```python
       model = genai.GenerativeModel(
       generation_config=genai.GenerationConfig(
               response_mime_type="text/x.enum",
               response_schema=Sentiment
           ))
       model = genai.GenerativeModel(
       'gemini-1.5-flash-latest',
       generation_config=genai.GenerationConfig(
           temperature=0.1,
           response_mime_type="application/json",
           response_schema=PizzaOrder,
       ))
      ```
  10. **ReAct: Reason and act** 
  
      ```python
      react_chat = model.start_chat()

      # You will perform the Action, so generate up to, but not including, the Observation.
      config = genai.GenerationConfig(stop_sequences=["\nObservation"])

      resp = react_chat.send_message(
          [model_instructions, example1, example2, question],
          generation_config=config,
          request_options=retry_policy)
      ```