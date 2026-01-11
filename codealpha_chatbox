# Task 2: FAQ Chatbot using NLP and Cosine Similarity

import nltk
import re
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.metrics.pairwise import cosine_similarity

# Download tokenizer (run once)
nltk.download('punkt')

# 1. Collect FAQs (Questions & Answers)
faqs = {
    "what is this project": "This project is an FAQ chatbot using NLP.",
    "what is a chatbot": "A chatbot is a program that answers user questions automatically.",
    "what language is used": "Python language is used for this chatbot.",
    "what is nlp": "NLP stands for Natural Language Processing.",
    "how does this chatbot work": "It matches user questions with FAQs using cosine similarity.",
    "who developed this project": "This project was developed as part of an internship task."
}

# 2. Preprocess text using NLP (lowercase, clean, tokenize)
def preprocess(text):
    text = text.lower()
    text = re.sub(r'[^\w\s]', '', text)
    tokens = nltk.word_tokenize(text)
    return " ".join(tokens)

questions = list(faqs.keys())
answers = list(faqs.values())

processed_questions = [preprocess(q) for q in questions]

# 3. Convert text to vectors using TF-IDF
vectorizer = TfidfVectorizer()
question_vectors = vectorizer.fit_transform(processed_questions)

print("🤖 FAQ Chatbot Ready (type 'exit' to quit)")

# 4. Chat loop
while True:
    user_input = input("You: ")

    if user_input.lower() == "exit":
        print("Bot: Goodbye!")
        break

    processed_input = preprocess(user_input)
    input_vector = vectorizer.transform([processed_input])

    similarity = cosine_similarity(input_vector, question_vectors)
    best_match = similarity.argmax()
    best_score = similarity[0][best_match]

    # 5. Display best matching answer
    if best_score > 0.2:
        print("Bot:", answers[best_match])
    else:
        print("Bot: Sorry, I don't understand the question.")
