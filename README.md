# Ex.no.8-Building-a-Simple-College-Admission-Chatbot
## Aim :
 To design, implement and test a simple rule-based chatbot in Python that answers frequently asked questions related to college admissions, such as courses offered, eligibility criteria, fees, application process, required documents, important dates, hostel facilities and contact details.
### Introduction
A chatbot is a software application that simulates a conversation with a human user, typically through text. A rule-based (or pattern-matching) chatbot works by comparing the user's message against a predefined set of keywords or patterns and returning a suitable pre-written response. It does not require large training datasets or heavy computation, which makes it an easy and beginner-friendly starting point for understanding how conversational AI systems are built. In this experiment, a College Admission Chatbot is developed to act as a virtual help-desk assistant that instantly answers common queries asked by prospective students.
### Procedure
    * Import the `re` and `random` libraries. The `re` module is used for pattern matching, and `random` is used to select responses randomly.
    
    * Create a **knowledge base** using a Python dictionary. Store different intents such as greeting, courses, eligibility, fees, application, documents, admission dates, hostel, contact details and goodbye.
    
    * For each intent, define **patterns** and **responses**. Patterns contain keywords or phrases that may appear in the user's question, while responses contain possible chatbot replies.
    
    * Create the `match_intent()` function to identify the user's intention. Convert the input into lowercase and use `re.search()` to compare the input with the available patterns.
    
    * Create the `get_response()` function to generate the chatbot's reply. It calls `match_intent()` and uses `random.choice()` to select a response from the matched intent.
    
    * If no matching intent is found, display a **fallback message** asking the user to ask an admission-related question.
    
    * Create a list of **sample queries** to test the chatbot. Include questions related to courses, eligibility, fees, application, documents, dates, hostel and contact details.
    
    * Execute the sample queries and display both the user's question and the chatbot's response to verify that the intents are correctly identified.
    
    * Create the interactive `chat()` function using `input()` to continuously receive questions from the user.
    
    * Display the chatbot response for each question and continue the conversation until the user enters **bye, exit, or quit**.
    
    * Execute the `chat()` function to start the **College Admission Chatbot** and interact with it in real time.

## Code
          import re
    import random
    
    knowledge_base = {
    
        "greeting": {
            "patterns": [
                r"\bhi\b",
                r"\bhello\b",
                r"\bhey\b",
                r"\bgood morning\b",
                r"\bgood evening\b"
            ],
            "responses": [
                "Hello! How can I help you with college admission?",
                "Hi! Welcome to the College Admission Chatbot.",
                "Hello! I can help you with admission-related information."
            ]
        },
    
        "courses": {
            "patterns": [
                r"\bcourse\b",
                r"\bcourses\b",
                r"\bprogram\b",
                r"\bprograms\b",
                r"\bdegree\b"
            ],
            "responses": [
                "We offer various UG and PG courses.",
                "Please check the college website for the complete list of available courses.",
                "Our college offers different undergraduate and postgraduate programs."
            ]
        },
    
        "eligibility": {
            "patterns": [
                r"\beligibility\b",
                r"\beligible\b",
                r"\bqualification\b",
                r"\bqualify\b"
            ],
            "responses": [
                "Eligibility depends on the selected course.",
                "The required qualification varies according to the course.",
                "Please check the admission requirements for your selected course."
            ]
        },
    
        "fees": {
            "patterns": [
                r"\bfee\b",
                r"\bfees\b",
                r"\bcost\b",
                r"\btuition\b",
                r"\bpayment\b"
            ],
            "responses": [
                "The fee structure depends on the selected course.",
                "Course fees vary depending on the program.",
                "Please contact the admission office for the exact fee details."
            ]
        },
    
        "application": {
            "patterns": [
                r"\bapply\b",
                r"\bapplication\b",
                r"\badmission process\b",
                r"\bhow to join\b",
                r"\bregister\b"
            ],
            "responses": [
                "You can apply through the college admission portal.",
                "The application can be completed through the official admission process.",
                "Please visit the college admission portal to apply."
            ]
        },
    
        "documents": {
            "patterns": [
                r"\bdocument\b",
                r"\bdocuments\b",
                r"\bcertificate\b",
                r"\bcertificates\b",
                r"\bproof\b"
            ],
            "responses": [
                "Required documents may include mark sheets, ID proof and certificates.",
                "Please keep your academic certificates and identity proof ready.",
                "The required documents depend on the admission process."
            ]
        },
    
        "dates": {
            "patterns": [
                r"\bdate\b",
                r"\bdates\b",
                r"\bdeadline\b",
                r"\blast date\b",
                r"\badmission date\b"
            ],
            "responses": [
                "Please check the official college website for admission dates.",
                "Admission deadlines are announced by the college.",
                "Please contact the admission office for the latest admission dates."
            ]
        },
    
        "hostel": {
            "patterns": [
                r"\bhostel\b",
                r"\baccommodation\b",
                r"\broom\b",
                r"\bstay\b"
            ],
            "responses": [
                "Yes, hostel facilities are available for students.",
                "Hostel accommodation is available. Please contact the college for details.",
                "You can contact the hostel office for room availability and fee details."
            ]
        },
    
        "contact": {
            "patterns": [
                r"\bcontact\b",
                r"\bphone\b",
                r"\btelephone\b",
                r"\bemail\b",
                r"\baddress\b"
            ],
            "responses": [
                "Please contact the college admission office for more details.",
                "You can contact the admission office for further information.",
                "Please check the official college website for contact details."
            ]
        },
    
        "goodbye": {
            "patterns": [
                r"\bbye\b",
                r"\bgoodbye\b",
                r"\bexit\b",
                r"\bquit\b",
                r"\bsee you\b"
            ],
            "responses": [
                "Goodbye! Have a nice day.",
                "Thank you for using the College Admission Chatbot. Goodbye!",
                "Bye! All the best for your admission."
            ]
        }
    }
    
    
    def match_intent(user_input):
        user_input = user_input.lower()
    
        for intent, data in knowledge_base.items():
            for pattern in data["patterns"]:
                if re.search(pattern, user_input):
                    return intent
    
        return None
    
    
    def get_response(user_input):
        intent = match_intent(user_input)
    
        if intent is not None:
            return random.choice(knowledge_base[intent]["responses"])
    
        return "Sorry, I did not understand your question. Please ask about courses, eligibility, fees, application, documents, dates, hostel or contact details."
    
    
    sample_queries = [
        "Hello",
        "What courses are available?",
        "What is the eligibility for admission?",
        "How much are the college fees?",
        "How can I apply for admission?",
        "What documents are required?",
        "What is the last date for admission?",
        "Is hostel facility available?",
        "How can I contact the college?",
        "Bye"
    ]
    
    
    print("=" * 60)
    print("COLLEGE ADMISSION CHATBOT - SAMPLE TEST")
    print("=" * 60)
    
    for query in sample_queries:
        print("\nYou :", query)
        print("Bot :", get_response(query))
    
    
    def chat():
        print("\n")
        print("=" * 60)
        print("WELCOME TO COLLEGE ADMISSION CHATBOT")
        print("=" * 60)
    
        print("You can ask about:")
        print("Courses")
        print("Eligibility")
        print("Fees")
        print("Application")
        print("Documents")
        print("Admission Dates")
        print("Hostel")
        print("Contact Details")
    
        print("\nType 'bye', 'exit' or 'quit' to end the chat.")
    
        while True:
            user_input = input("\nYou : ")
    
            response = get_response(user_input)
    
            print("Bot :", response)
    
            intent = match_intent(user_input)
    
            if intent == "goodbye":
                break
    
    
    chat()
 ## Output
 <img width="715" height="747" alt="image" src="https://github.com/user-attachments/assets/df63412b-f987-4e97-960f-a4bf55e8eaed" />
 <img width="592" height="392" alt="image" src="https://github.com/user-attachments/assets/7381f129-9ff1-4dd8-ad03-d0771748e718" />

## Conclusion
Thus, a simple rule-based College Admission Chatbot was successfully designed, implemented and tested using Python. The chatbot uses a keyword/pattern-based knowledge base to identify the intent behind a user's question and responds with an appropriate, pre-defined answer covering courses, eligibility, fees, application process, documents, dates, hostel and contact information. The experiment demonstrates the fundamental building blocks — knowledge base design, intent matching and response generation — on which more advanced NLP-based and AI-based chatbots are built.









