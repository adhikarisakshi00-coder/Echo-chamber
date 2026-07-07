# Echo Chamber 9000

A simple interactive Streamlit app built as part of the MirAI School of Technology
Virtual Summer Internship 2026 — "AI Builder" Track (Assignment: The Identity Echo Interface).

The app collects a user's name and message, waits for an explicit "Transmit" action,
validates the inputs, and displays a personalized confirmation — along with an estimated
token cost for the message, calculated using the standard "1 token ≈ 4 characters" heuristic.

## Features

- **Text inputs** for Name and Message
- **Action gate**: nothing happens until the Transmit button is clicked
- **Input validation**:
  - Empty Name → error message
  - Empty Message (with Name filled) → warning message
- **Success output**: personalized greeting echoing back the submitted message
- **Token Cost Estimator**: estimates how many tokens the message would consume in an AI context window

## Setup

1. Install dependencies:
   
   ```bash
   python -m pip install streamlit
   ```
2. Run app.py

```bash
streamlit run app.py
```

3. This will start a local server and open the app in your browser at:

```
http://localhost:8501
```

## Usage

1. Enter your **Name** in the first field.
2. Enter a **Message** in the second field.
3. Click **Transmit**.
4. Based on your inputs:
   - If Name is empty → an error is shown asking for a name.
   - If Name is filled but Message is empty → a warning is shown asking for a message.
   - If both fields are filled → a success message is displayed, along with the estimated token count for your message.

## Example

**Input:**
- Name: `Sia`
- Message: `hello world`

**Output:**
```
Transmission successful! Greetings, Sia. We received your message: hello world
System Check: Your message will consume approximately 2 tokens from our context window.
```

## Token Estimation Logic

```python
token_count = len(user_message) // 4
```

This uses integer division on the character count of the message, following the
"~4 characters per token" rule of thumb commonly used to estimate AI API costs.

## Project Structure

```
.
├── app.py        # Main Streamlit application
└── README.md      # This file
```

## Notes

- All output logic is gated behind the Transmit button — no output appears until it's clicked.
- Validation checks Name before Message, so if both fields are empty, the Name error takes priority.
