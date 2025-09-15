Conversation Classification and Summarization
Overview

This project demonstrates two tasks:

1. Conversation Classification (Information Extraction) – Extracts user details like name, age, location, email, and phone from chat text.

2. Conversation Summarization – Produces short summaries of conversations, highlighting topics, user concerns, and assistant suggestions.


# Files Structure

  classification.py – Extracts structured user details.

  summarizer.py – Summarizes conversations.

  README

# Features

## Classification

Extracts name, age, location, email, phone.

Handles missing values by marking them as "unclear".

Always outputs clean JSON.

Example:

Input: "Hi, I’m Priya Verma, 30, living in Mumbai. Email: priya.v@gmail.com"
Output: {
  "name": "Priya Verma",
  "age": 30,
  "location": "Mumbai",
  "email": "priya.v@gmail.com",
  "phone": "unclear"
}

## Summarization

Summarizes conversations every few turns.

Captures main points in 2–4 sentences.

Falls back to a short snippet if summarization fails.

Example:

[Summary after 3 turns]: The main topic discussed is the user's fatigue. The user's main concern is their sleep schedule, specifically sleeping only 5 hours on weekdays. The assistant's recommendation is unclear, as the conversation does not provide further guidance.

[Summary after 6 turns]: The main topic discussed is sleep and diet. The user's main concern is their sleep schedule and diet, specifically eating mostly fast food. The assistant's recommendations are to aim for 7-8 hours of sleep and to include fruits, vegetables, and lean protein in their diet.
 

# How to Run

Install requirements:

pip install openai , jsonschema


Run classification examples:

python examples.py


Run summarizer example:

from summarizer import ConversationManager

cm = ConversationManager()
cm.add_message("user", "Hi, I’m Rahul Sharma, 24, from Delhi.")
cm.add_message("assistant", "Got it! I’ll save your details.")
cm.create_summary()

print(cm.get_summaries())

