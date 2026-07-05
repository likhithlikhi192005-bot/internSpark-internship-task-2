API-Data-Fetcher/
│── app.py
│── requirements.txt
│── README.md
│── screenshots/
│   └── output.png   (Add your screenshot after running)
import requests

BASE_URL = "https://jsonplaceholder.typicode.com/users"

def fetch_users():
    try:
        response = requests.get(BASE_URL)
        response.raise_for_status()
        return response.json()
    except requests.exceptions.RequestException as e:
        print("Error fetching data:", e)
        return []

def display_users(users):
    if not users:
        print("No users found.")
        return

    print("\nUser Details")
    print("-" * 60)

    for user in users:
        print(f"Name    : {user['name']}")
        print(f"Username: {user['username']}")
        print(f"Email   : {user['email']}")
        print(f"City    : {user['address']['city']}")
        print("-" * 60)

def search_users(users, keyword):
    keyword = keyword.lower()

    filtered = [
        user for user in users
        if keyword in user['name'].lower()
        or keyword in user['username'].lower()
        or keyword in user['address']['city'].lower()
    ]

    return filtered

def main():
    users = fetch_users()

    if not users:
        return

    while True:
        print("\n===== API Data Fetcher =====")
        print("1. Display All Users")
        print("2. Search User")
        print("3. Exit")

        choice = input("Enter your choice: ")

        if choice == "1":
            display_users(users)

        elif choice == "2":
            keyword = input("Enter Name/Username/City: ")
            result = search_users(users, keyword)
            display_users(result)

        elif choice == "3":
            print("Goodbye!")
            break

        else:
            print("Invalid Choice")

if __name__ == "__main__":
    main()
    # API Data Fetcher using Python Requests

## 📌 Project Overview

This project demonstrates how to fetch data from a REST API using Python's **requests** library. The application retrieves user information from the JSONPlaceholder API, parses the JSON response, and displays the data in a readable format. It also includes a search feature to filter users by name, username, or city.

---

## 🚀 Features

- Fetch data from a public REST API
- Parse JSON responses
- Display formatted user information
- Search users by:
  - Name
  - Username
  - City
- Error handling for failed API requests

---

## 🛠 Technologies Used

- Python 3
- Requests Library
- JSONPlaceholder API

---

## 📂 Project Structure

```
API-Data-Fetcher/
│── app.py
│── requirements.txt
│── README.md
│── screenshots/
│   └── output.png
```

---

## ▶ Installation

Clone the repository:

```bash
git clone https://github.com/yourusername/API-Data-Fetcher.git
```

Move into the project folder:

```bash
cd API-Data-Fetcher
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Run the application:

```bash
python app.py
```

---

## Sample Output

```
===== API Data Fetcher =====

1. Display All Users
2. Search User
3. Exit

Enter Choice: 1

----------------------------------------------------
Name    : Leanne Graham
Username: Bret
Email   : Sincere@april.biz
City    : Gwenborough
----------------------------------------------------
```

---

## API Used

https://jsonplaceholder.typicode.com/users

---

## Learning Outcomes

- Working with REST APIs
- HTTP GET requests
- JSON Parsing
- Data filtering
- Error Handling
- Python Programming

---

## Author

git init

git add .

git commit -m "Completed API Data Fetcher Project"

git branch -M main

git remote add origin https://github.com/<your-username>/API-Data-Fetcher.git

git push -u origin main
