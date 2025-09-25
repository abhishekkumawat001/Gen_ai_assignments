# Gen AI Assignments Repository

This repository contains assignments focused on **Generative AI Prompting Techniques** and structured JSON output generation using Large Language Models (LLMs).

## Repository Overview

This repository demonstrates advanced prompting strategies for reliable and structured AI responses, covering various techniques essential for production-grade AI applications.

## Assignment 1: Advanced Prompting Techniques

Assignment 1 focuses on designing robust prompts that generate strictly valid JSON outputs matching specific schemas and constraints. The assignment covers five key areas of prompt engineering:

### Core Requirements

- **JSON Output**: All tasks must produce strictly valid JSON matching required schemas
- **No External Access**: All tasks must be solvable without web access
- **Self-contained Prompts**: Prompts must be robust to adversarial or ambiguous inputs
- **Role Conditioning**: Proper system/user prompt separation

### Tasks Overview

#### Task T1: Role Conditioning - System vs User Separation
**Objective**: Design system and user prompts for generating educational content in a specific voice.

**Focus**: Backpropagation explanation in "Socratic, critical reviewer" voice
- ≤90 words explanation ending with a probing question
- Must mention "gradient" or "derivative"
- No mathematical symbols or code blocks
- Questioning and analytical tone

**JSON Schema**:
```json
{
  "voice": "string, must be 'Socratic, critical reviewer'",
  "explanation": "string, ≤100 words about backpropagation",
  "ending_question": "string, must end with ?"
}
```

#### Task T2: Robust Function Calling with Assumptions
**Objective**: Create prompts for mathematical conversions with explicit assumptions.

**Focus**: Temperature conversion (Celsius to Fahrenheit)
- Accurate conversion with formula explanation
- 40-80 word explanation covering assumptions
- Discussion of linear scale, precision considerations

**JSON Schema**:
```json
{
  "result": "number (int or float)",
  "formula": "string, the conversion formula used",
  "explanation": "string, 40≤words≤80, covering assumptions and process"
}
```

#### Task T3: Few-Shot Learning - Support Ticket Classification
**Objective**: Design classification prompts using different few-shot approaches.

**Focus**: Customer support ticket categorization (Technical|Billing|General|Urgent)
- Three variants: zero-shot, one-shot, and multi-shot
- Realistic confidence scoring (0.6-0.95 range)
- ≤30 word rationale for classification

**JSON Schema**:
```json
{
  "label": "string, one of: Technical|Billing|General|Urgent",
  "confidence": "number, 0.0-1.0",
  "rationale": "string, ≤30 words explaining the classification"
}
```

#### Task T4: Few-Shot Information Extraction
**Objective**: Extract structured data from unstructured professional profiles.

**Focus**: Resume/profile parsing with graceful error handling
- Handle missing or ambiguous information
- Email validation (proper format or null)
- Experience normalization (handle "about 5 years" → 5)
- Skills extraction and normalization

**JSON Schema**:
```json
{
  "name": "string, extracted full name",
  "email": "string or null, valid email format or null if missing",
  "years_experience": "integer, 0-50 range",
  "top_3_skills": "array of strings, exactly 3 items, lowercase",
  "last_company": "string or 'unknown' if not mentioned"
}
```

#### Task T5: Safety and Refusal - Harmful Content Detection
**Objective**: Design safety-focused prompts that identify and refuse harmful requests.

**Focus**: Content moderation with constructive alternatives
- Detect potentially harmful requests
- Provide clear policy explanations
- Offer ≥2 safe alternatives
- Handle deceptive authority claims and social engineering

**JSON Schema**:
```json
{
  "decision": "string, either 'allow' or 'refuse'",
  "policy_basis": "string, ≤40 words explaining the policy reason",
  "safe_alternatives": "array of strings, ≥2 constructive alternatives",
  "explanation": "string, ≤40 words, helpful response to user"
}
```

## Technical Setup

### Dependencies
- Python 3.x
- PyTorch
- Transformers library
- Outlines (version 1.2.2)
- Pydantic for schema validation

### Model Used
- **LiquidAI/LFM2-350M**: A 350M parameter language model for structured generation

### Installation
```bash
pip install outlines==1.2.2
pip install torch transformers pydantic
```

## File Structure

```
├── Assignment_1.ipynb          # Main assignment notebook with all tasks
├── answers_24401.json         # Generated JSON outputs for all tasks
└── README.md                  # This documentation file
```

## Usage Instructions

1. **Setup Environment**: Install required dependencies
2. **Open Notebook**: Launch `Assignment_1.ipynb` in Jupyter
3. **Set Roll Number**: Update the `ROLL_NO` variable
4. **Run Tasks**: Execute cells sequentially to complete all tasks
5. **Verify Output**: Check generated `answers_{ROLL_NO}.json` file

## Key Learning Outcomes

This assignment demonstrates mastery of:

- **Prompt Engineering**: Crafting precise prompts for reliable outputs
- **JSON Schema Compliance**: Ensuring strict adherence to data structures
- **Few-Shot Learning**: Leveraging examples for better model performance
- **Safety Considerations**: Building responsible AI interactions
- **Error Handling**: Managing ambiguous or missing information gracefully

## Prompting Techniques Covered

1. **Role Conditioning**: System vs user prompt separation
2. **Few-Shot Learning**: Zero-shot, one-shot, and multi-shot approaches
3. **Structured Output**: JSON schema compliance and validation
4. **Safety Filtering**: Harmful content detection and refusal
5. **Information Extraction**: Parsing unstructured data reliably
6. **Assumption Handling**: Explicit reasoning about edge cases

## Academic Integrity

This repository contains completed assignment work. Please use for reference and learning purposes while adhering to your institution's academic integrity policies.
