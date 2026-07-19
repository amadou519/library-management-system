# 📚 Library Management System

A full-stack web application for managing a library's books, students, and loan records — built with Python and Django.

---

## 🔍 Overview

This application provides a complete library management solution with two distinct user roles: **Admin** and **Student**. Admins manage the book inventory and track loans, while students can register, browse available books, and view their borrowing history. The system automatically calculates overdue fines based on loan duration.

---

## ✨ Features

### Admin
- Secure admin login with superuser authentication
- Add, view, and delete books from the inventory
- View and manage registered students
- Issue books to students and track all active loans
- Automatic overdue fine calculation ($5/day after 14-day loan period)
- View a detailed issued-books dashboard with fine status per student

### Student
- Self-registration with profile photo upload
- Secure student login and session management
- View personal profile with editable details (email, phone, branch, class)
- View currently issued books with due dates and any applicable fines
- Secure password change functionality

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Backend | Python 3.10, Django 4.x |
| Database | SQLite3 (via Django ORM) |
| Frontend | HTML5, CSS3, Django Templates |
| Authentication | Django built-in auth (`django.contrib.auth`) |
| File handling | Django `ImageField`, media file management |
| Architecture | MVT (Model-View-Template) |

---

## 🗄️ Data Models

### `Book`
| Field | Type | Description |
|---|---|---|
| `name` | CharField | Title of the book |
| `author` | CharField | Author name |
| `isbn` | PositiveIntegerField | Unique ISBN identifier |
| `category` | CharField | Book category/genre |

### `Student`
| Field | Type | Description |
|---|---|---|
| `user` | OneToOneField (User) | Linked Django auth user |
| `classroom` | CharField | Student's class |
| `branch` | CharField | Academic branch |
| `roll_no` | CharField | Roll number |
| `phone` | CharField | Contact number |
| `image` | ImageField | Profile photo |

### `IssuedBook`
| Field | Type | Description |
|---|---|---|
| `student_id` | CharField | Reference to student |
| `isbn` | CharField | Reference to book ISBN |
| `issued_date` | DateField | Auto-set on issue |
| `expiry_date` | DateField | Auto-set to issued + 14 days |

---

## 📁 Project Structure

```
Library_Management_Using_DjangoPython/
│
├── library/                    # Main Django app
│   ├── models.py               # Book, Student, IssuedBook models
│   ├── views.py                # All view logic (admin + student)
│   ├── urls.py                 # URL routing
│   ├── forms.py                # Book issue form
│   ├── admin.py                # Django admin registration
│   ├── templates/              # HTML templates
│   │   ├── index.html
│   │   ├── admin_login.html
│   │   ├── student_login.html
│   │   ├── student_registration.html
│   │   ├── add_book.html
│   │   ├── view_books.html
│   │   ├── issue_book.html
│   │   ├── view_issued_book.html
│   │   ├── profile.html
│   │   └── ...
│   ├── static/                 # Static assets
│   └── media/                  # Uploaded profile images
│
├── LibraryManagementSystem/    # Django project config
│   ├── settings.py
│   ├── urls.py
│   ├── wsgi.py
│   └── asgi.py
│
├── manage.py
└── db.sqlite3
```

---

## 🚀 Getting Started

### Prerequisites
- Python 3.8+
- pip

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/YOUR_USERNAME/library-management-system.git
cd library-management-system

# 2. Create and activate a virtual environment
python -m venv venv
source venv/bin/activate        # On Windows: venv\Scripts\activate

# 3. Install dependencies
pip install django pillow

# 4. Apply migrations
python manage.py migrate

# 5. Create an admin superuser
python manage.py createsuperuser

# 6. Run the development server
python manage.py runserver
```

### Access the app
- Home page: `http://127.0.0.1:8000/`
- Admin login: `http://127.0.0.1:8000/admin_login`
- Student registration: `http://127.0.0.1:8000/student_registration`

---

## 📸 Screenshots

> *(Add screenshots of the home page, admin dashboard, student profile, and issued books view here)*

---

## 🔒 Security Notes

> ⚠️ This project was built for learning purposes. Before deploying to production:
> - Replace the `SECRET_KEY` in `settings.py` with a secure environment variable
> - Set `DEBUG = False`
> - Configure `ALLOWED_HOSTS` with your domain
> - Migrate from SQLite to PostgreSQL or MySQL for production use

---

## 🧠 Key Concepts Demonstrated

- Django MVT architecture
- Django ORM with relational data models
- Role-based access control (Admin vs. Student) using Django's auth system
- Session management and login/logout flows
- File upload and media handling with `ImageField`
- Business logic implementation (fine calculation based on date arithmetic)
- CRUD operations across multiple related models
- Form validation and user feedback

---

## 👨‍💻 Author

**Amadou Bah**  
Software Engineer | Full-Stack Developer  
[LinkedIn](https://www.linkedin.com/in/amadoubah519) · [GitHub](https://github.com/YOUR_USERNAME)
