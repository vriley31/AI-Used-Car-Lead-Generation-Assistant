# AI-Used-Car-Lead-Generation-Assistant

This project uses Python, Natural Language Processing (NLP), and SQLite to create an AI-powered virtual assistant for a used car dealership. The chatbot helps customers find vehicles, answer frequently asked questions, collect lead information, provide financing details, and retrieve inventory information from a database.

The goal is to improve customer engagement, automate lead generation, and provide instant access to dealership information while reducing manual workload for sales representatives.

---

## Key Features

1. Built a conversational AI chatbot using Python.
2. Created an intent-based NLP model using JSON training data.
3. Developed a SQLite database to store vehicle inventory.
4. Designed a customer lead management system.
5. Implemented CRUD operations (Create, Read, Update, Delete).
6. Added dealership FAQs and knowledge repository.
7. Integrated vehicle inventory searches into chatbot responses.
8. Implemented financing, trade-in, warranty, and test-drive inquiries.
9. Added error handling for database operations.
10. Created an expandable architecture for future machine learning enhancements.

---

## Database Design

The chatbot uses SQLite as its backend database.

### Inventory Table

| Field | Data Type |
|---------|---------|
| id | INTEGER |
| make | TEXT |
| model | TEXT |
| year | INTEGER |
| price | REAL |
| availability | TEXT |

### Leads Table

| Field | Data Type |
|---------|---------|
| id | INTEGER |
| name | TEXT |
| contact | TEXT |
| interest | TEXT |
| timestamp | DATETIME |

### FAQ Table

| Field | Data Type |
|---------|---------|
| id | INTEGER |
| question | TEXT |
| answer | TEXT |

---

## Technologies Used

- Python
- SQLite
- JSON
- NLTK
- NumPy
- Pandas
- TensorFlow / Keras
- Git
- GitHub

---

## Sample Inventory

| Year | Make | Model |
|------|------|------|
| 2020 | Honda | Accord EX |
| 2018 | Toyota | Camry SE |
| 2021 | Ford | F-150 XLT |
| 2019 | Chevrolet | Tahoe LT |
| 2022 | Nissan | Rogue SV |
| 2017 | Jeep | Grand Cherokee Limited |
| 2023 | Tesla | Model 3 Long Range |
| 2020 | BMW | X5 M Sport |
| 2019 | Mercedes-Benz | C300 |
| 2021 | Subaru | Outback Premium |

---

## Example Customer Questions

- What vehicles do you have available?
- Do you offer financing?
- Can I schedule a test drive?
- What is your cheapest vehicle?
- Do you accept trade-ins?
- What are your business hours?
- Do your vehicles come with a warranty?
- Do you have any SUVs available?

---

## Project Structure

```text
AI-Used-Car-Lead-Generation-Assistant/
│
├── chatbot.py
├── intents.json
├── database.py
├── populate_data.py
├── chatbot.db
├── requirements.txt
├── README.md
│
├── models/
│   └── chatbot_model.keras
│
├── data/
│   ├── inventory.csv
│   └── faq_data.csv
│
└── screenshots/
    ├── chatbot_demo.png
    ├── inventory_search.png
    ├── lead_capture.png
    └── database_schema.png
```

---

## Example Code

### Retrieve Available Vehicles

```python
def get_inventory():
    conn = sqlite3.connect("chatbot.db")
    cursor = conn.cursor()

    cursor.execute(
        "SELECT * FROM inventory WHERE availability='Available'"
    )

    cars = cursor.fetchall()
    conn.close()

    return cars
```

### Capture Customer Lead

```python
def insert_lead(name, contact, interest):
    conn = sqlite3.connect("chatbot.db")
    cursor = conn.cursor()

    cursor.execute(
        "INSERT INTO leads (name, contact, interest) VALUES (?, ?, ?)",
        (name, contact, interest)
    )

    conn.commit()
    conn.close()
```

---

## Business Value

This solution demonstrates how artificial intelligence and databases can be combined to:

- Increase lead generation opportunities.
- Improve customer experience.
- Reduce dealership response times.
- Centralize inventory management.
- Automate repetitive customer service tasks.
- Support sales representatives with qualified leads.

---

## Future Enhancements

- Integration with dealership CRM systems.
- Real-time inventory updates.
- Voice-enabled chatbot support.
- Vehicle recommendation engine.
- Machine learning lead scoring.
- Sentiment analysis for customer interactions.
- Web deployment using Flask or Streamlit.

---

## Author

**Victoria Riley**

Graduate Student | Data Analytics & Predictive Modeling

GitHub: [@vriley31](https://github.com/vriley31)

---
⭐ If you found this project interesting, consider giving it a star!
