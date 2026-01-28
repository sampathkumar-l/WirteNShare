# WriteNShare - Full Featured Web Application

A complete, production-ready blog application built with Flask, featuring user authentication, blog post management, profile customization, and more.

## Features

- **User Authentication**
  - User registration with form validation
  - Secure login/logout functionality
  - Password hashing with Bcrypt
  - "Remember Me" functionality

- **User Profiles**
  - Customizable user profiles
  - Profile picture upload and resizing
  - View all posts by a specific user

- **Blog Post Management**
  - Create new blog posts
  - Read and view posts with pagination
  - Update your own posts
  - Delete your own posts with confirmation modal
  - Rich content formatting

- **Password Reset**
  - Email-based password reset
  - Secure token generation
  - Time-limited reset links

- **Additional Features**
  - Responsive design with Bootstrap 5
  - Custom CSS styling
  - Error handling (404, 403, 500)
  - Database integration with SQLAlchemy
  - Form validation with WTForms
  - Pagination for post listings

## Project Structure

```
WriteNShare/
│
├── writeNshare/
│   ├── __init__.py              # Application factory and config
│   ├── models.py                # Database models (User, Post)
│   │
│   ├── main/
│   │   ├── __init__.py
│   │   └── routes.py            # Home and About routes
│   │
│   ├── users/
│   │   ├── __init__.py
│   │   ├── forms.py             # User forms (Registration, Login, etc.)
│   │   ├── routes.py            # User routes (auth, profile, etc.)
│   │   └── utils.py             # Helper functions (save pictures, emails)
│   │
│   ├── posts/
│   │   ├── __init__.py
│   │   ├── forms.py             # Post forms
│   │   └── routes.py            # Post CRUD routes
│   │
│   ├── errors/
│   │   ├── __init__.py
│   │   └── handlers.py          # Error handlers
│   │
│   ├── static/
│   │   ├── main.css             # Custom CSS
│   │   └── profile_pics/        # User profile pictures
│   │       └── default.jpg
│   │
│   └── templates/
│       ├── layout.html          # Base template
│       ├── home.html            # Home page with posts
│       ├── about.html           # About page
│       ├── register.html        # Registration form
│       ├── login.html           # Login form
│       ├── account.html         # User account page
│       ├── create_post.html     # Create/Update post form
│       ├── post.html            # Single post view
│       ├── user_posts.html      # User's posts listing
│       ├── reset_request.html   # Password reset request
│       ├── reset_token.html     # Password reset form
│       └── errors/
│           ├── 403.html
│           ├── 404.html
│           └── 500.html
│
├── run.py                       # Application entry point
├── requirements.txt             # Python dependencies
├── .gitignore                   # Git ignore rules
└── README.md                    # This file
```

## Installation

### Prerequisites

- Python 3.8 or higher
- pip (Python package installer)

### Setup Steps

1. **Clone or download the project**
   ```bash
   cd flask_blog_complete
   ```

2. **Create a virtual environment**
   ```bash
   python -m venv venv
   ```

3. **Activate the virtual environment**
   - On Windows:
     ```bash
     venv\Scripts\activate
     ```
   - On macOS/Linux:
     ```bash
     source venv/bin/activate
     ```

4. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

5. **Set environment variables (Optional)**
   
   For email functionality, set these environment variables:
   ```bash
   # On Windows (CMD)
   set EMAIL_USER=your-email@gmail.com
   set EMAIL_PASS=your-app-password

   # On Windows (PowerShell)
   $env:EMAIL_USER="your-email@gmail.com"
   $env:EMAIL_PASS="your-app-password"

   # On macOS/Linux
   export EMAIL_USER=your-email@gmail.com
   export EMAIL_PASS=your-app-password
   ```

   **Note:** For Gmail, you'll need to use an [App Password](https://support.google.com/accounts/answer/185833) instead of your regular password.

6. **Run the application**
   ```bash
   python run.py
   ```

7. **Access the application**
   Open your browser and go to: `http://127.0.0.1:5000`

## Usage

### First Time Setup

1. Navigate to the register page and create an account
2. Log in with your credentials
3. Update your profile picture in the Account page (optional)
4. Start creating blog posts!

### Creating Posts

1. Click "New Post" in the navigation bar
2. Fill in the title and content
3. Click "Post" to publish

### Managing Posts

- View all your posts by clicking on your username
- Update or delete posts from the individual post page
- Only you can edit or delete your own posts

### Password Reset

If you forget your password:
1. Click "Forgot Password?" on the login page
2. Enter your email address
3. Check your email for the reset link
4. Follow the link and set a new password

## Database

The application uses SQLite by default (`site.db`). The database is automatically created when you first run the application.

### Database Models

**User**
- id (Primary Key)
- username (Unique)
- email (Unique)
- image_file (Profile picture filename)
- password (Hashed)
- posts (Relationship to Post model)

**Post**
- id (Primary Key)
- title
- date_posted
- content
- user_id (Foreign Key to User)

## Configuration

You can modify configuration settings in `flaskblog/__init__.py`:

- `SECRET_KEY`: Used for session management and CSRF protection
- `SQLALCHEMY_DATABASE_URI`: Database connection string
- `MAIL_SERVER`, `MAIL_PORT`, etc.: Email configuration for password reset

## Security Features

- Password hashing with Bcrypt
- CSRF protection on all forms
- Login required decorators for protected routes
- Secure session management
- SQL injection protection through SQLAlchemy ORM
- File upload validation (profile pictures)
- Authorization checks (users can only edit their own posts)

## Deployment Considerations

For production deployment:

1. Change the `SECRET_KEY` to a secure random value
2. Use a production-grade database (PostgreSQL, MySQL)
3. Set `debug=False` in `run.py`
4. Use a production WSGI server (Gunicorn, uWSGI)
5. Configure proper email settings
6. Set up HTTPS
7. Configure environment variables properly
8. Use a reverse proxy (Nginx)

## Technologies Used

- **Flask**: Web framework
- **SQLAlchemy**: ORM for database operations
- **Flask-Login**: User session management
- **Flask-Bcrypt**: Password hashing
- **Flask-WTF**: Form handling and validation
- **Flask-Mail**: Email functionality
- **Pillow**: Image processing
- **Bootstrap 5**: Frontend framework



