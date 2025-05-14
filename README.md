# Exno.8-Prompt-Engg
## Date:
## Register no: 212222230066
# Aim: 
To develop a prompt-based application using ChatGPT – demonstrating how to create a prompt-driven assistant for organizing daily tasks, with progression from basic to advanced prompt designs.To explore how various prompting techniques can be used to generate and manipulate audio content (e.g., music, sound effects, voice narration) using AI models.
# Algorithm: 
Design and implement Python-based applications that:

1. Accept user input as a prompt.

2. Interact with AI models (ChatGPT for task management, audio-focused models for sound generation).

3. Receive responses with task suggestions or generated audio content.

4. Store, organize, and optionally download outputs.

5. Demonstrate progression from simple to advanced prompts.

# Objective:

## Build ChatGPT-powered assistant that:
a. Organizes user-input daily tasks.
b. Evolves with progressively advanced prompt engineering.
c. Outputs categorized, prioritized, and optimized to-do lists.
d. Logs data for reuse and review.

## Build an AI audio content generator that:
a. Accepts user prompts for music, narration, or effects.
b. Interfaces with audio generation APIs.
c. Saves or plays audio.

## Step-by-Step Implementation – Task Manager:

## Step 1: Set Up API Access

Create an OpenAI account

Obtain your API key.

Install necessary Python libraries:
```
pip install openai python-dotenv
```
Store your API key in a .env file:
```
OPENAI_API_KEY=your_openai_key_here
```
## Step 2: Basic Prompt – Simple Task Listing
```
import os
import openai
from dotenv import load_dotenv

load_dotenv()
openai.api_key = os.getenv("OPENAI_API_KEY")

def ask_chatgpt(prompt):
    response = openai.ChatCompletion.create(
        model="gpt-4",
        messages=[{"role": "user", "content": prompt}]
    )
    return response['choices'][0]['message']['content']
```
### Basic prompt
```
simple_prompt = "Organize my tasks: buy groceries, finish homework, call mom."
response = ask_chatgpt(simple_prompt)
print("\nSimple Response:\n", response)
```
## Step 3: Intermediate Prompt – Add Prioritization and Deadlines
```
intermediate_prompt = (
    "Organize and prioritize these tasks based on urgency and time required: "
    "1. Buy groceries, 2. Finish homework (due tomorrow), 3. Call mom, 4. Reply to emails, 5. Exercise for 30 minutes."
)
response = ask_chatgpt(intermediate_prompt)
print("\nIntermediate Response:\n", response)
```
## Step 4: Advanced Prompt – Include Categorization, Time Blocks, Suggestions
```
advanced_prompt = (
    "Create a daily schedule using time blocks for the following tasks. Categorize them as personal, academic, or health. "
    "Include any optimization tips: 1. Finish AI assignment (due at 5 PM), 2. Gym session, 3. Buy vegetables, 4. Team meeting at 11 AM, 5. Review notes, 6. Meditation."
)
response = ask_chatgpt(advanced_prompt)
print("\nAdvanced Response:\n", response)
```
## Step 5: Logging Responses
```
import json
from datetime import datetime

def log_response(prompt, response):
    entry = {
        "timestamp": str(datetime.now()),
        "prompt": prompt,
        "response": response
    }
    with open("task_log.json", "a") as f:
        json.dump(entry, f)
        f.write("\n")

log_response(advanced_prompt, response)
```
## Step-by-Step Implementation – Audio Generation:

## Step 1: Choose an AI Tool for Audio (e.g., ElevenLabs, Bark, Google TTS)

Register and obtain API key.

Install required libraries (example with ElevenLabs):
```
pip install elevenlabs
```
## Step 2: Generate Audio with Prompt Input
```
from elevenlabs import generate, play, set_api_key
import os

set_api_key(os.getenv("ELEVENLABS_API_KEY"))

def generate_audio(prompt_text):
    audio = generate(
        text=prompt_text,
        voice="Rachel",  # or any available voice
        model="eleven_monolingual_v1"
    )
    play(audio)

prompt_text = "Hello! This is your AI narrator helping you stay productive today."
generate_audio(prompt_text)
```
# Result:

The application successfully demonstrates:

1. Task organization with ChatGPT.

2. Audio narration generation using advanced prompting.

3. Integration of language and voice models in one workflow.

# Conclusion:
This experiment shows how various prompting techniques can be effectively used to build AI-powered applications. In this case:

1. ChatGPT helps structure daily life with natural prompts.

2. Audio APIs bring those prompts to life through narration or sound design.

3. The approach is scalable to music composition, audio books, or accessibility tools.
