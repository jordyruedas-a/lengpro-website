
## 📋 Executive Summary

This project is a fully functional, responsive web application built using the **Flask micro-framework**. It serves as an interactive educational portfolio focused on the history, paradigms, and technical ecosystems of programming languages. 

The front-end features a dynamic timeline, a card-based layout for technical content, a video gallery, and a working contact form. The back-end handles dynamic route rendering, static file serving, and a secure email dispatching system using Flask-Mail.



## 🧩 Project Architecture

The repository follows a standard Flask application structure:


```
Lenguajes_Web_App/
├── app.py # Main Flask application entry point
├── .env # Environment variables (email credentials)
├── static/ # Static assets served directly
│ ├── styles.css # Global CSS styles & responsive design
│ ├── app.js # Client-side JavaScript (UI interactivity)
│ ├── 1.pdf, 2.pdf, ... # PDF resources for downloadable activities
│ ├── 1.jpg, 2.jpg, ... # Timeline and UI images
│ ├── video.mp4 # Background video for hero section
│ └── *.mp4 # Additional video resources
└── templates/
└── index.html # Main HTML template (Jinja2 markup)

```



## 🚀 Module Breakdown & Technical Deep Dive

### 1. Back-End Architecture (Flask & Routing)
- **Core Logic (`app.py`):** The entry point that initializes the Flask app, configures the email server, and defines the main route (`/`) which renders the `index.html` template.
- **Email Integration:** Uses `Flask-Mail` with environment variables (`MAIL_USERNAME`, `MAIL_PASSWORD`) loaded from a `.env` file. 
- **AJAX Form Handling:** The contact form submits data asynchronously via a `POST` request to the `/send_email` endpoint. The back-end processes the form data, sends the email, and returns a textual response (success or error) to the front-end, allowing for a seamless user experience without page reloads.

### 2. Front-End Architecture (HTML, CSS, JS)
- **Responsive Navigation:** A `navbar` component with a hidden burger menu (`display: flex` vs `display: none`) toggled via JavaScript for mobile devices.
- **Dynamic Timeline (`timeline-section`):**
  - Built with CSS `linear-gradient` to create a vertical center line.
  - Uses CSS `backdrop-filter: blur(10px)` for glassmorphism effects.
  - Implements a staggered entrance animation using an `IntersectionObserver` in JavaScript. Elements fade and slide in as the user scrolls down.
- **Curiosity Carousel:**
  - A rotating text carousel that cycles through programming facts using `setInterval` and `CSS transitions`.
- **Video Gallery:** 
  - Uses embedded `<iframe>` elements from YouTube with `position: relative` and `padding-bottom: 56.25%` to maintain a 16:9 aspect ratio automatically.
- **PDF Preview:** 
  - Each activity card features an `<embed>` element that renders a preview of the PDF file directly in the browser, along with a styled download button.

### 3. Responsive Design Strategy
- **Grid Layouts:** The `cards` section uses CSS Grid (`grid-template-columns: repeat(auto-fit, minmax(200px, 1fr))`) to auto-adapt the number of columns based on the screen width.
- **Conditional Styling:** The `@media (max-width: 768px)` breakpoint transitions the timeline from a double-sided zigzag layout to a single-column mobile-friendly layout, and converts the navigation bar to a mobile hamburger menu.



## ⚙️ Environment Setup & Dependencies

### 1. Prerequisites
- Python 3.9 or higher.
- A Gmail account with "App Passwords" enabled (for the email backend).
- A `.env` file created in the root directory with the following variables:

MAIL_USERNAME=your_email@gmail.com
MAIL_PASSWORD=your_app_password

2. Installation

To run this project locally, set up a Python virtual environment and install the dependencies:
bash

# 1. Create a virtual environment
python -m venv venv

# 2. Activate the environment
# Windows:
venv\Scripts\activate
# Mac/Linux:
source venv/bin/activate

# 3. Install the required dependencies
pip install flask flask-mail python-dotenv

## 📊 Key Technical Variables Explained
Variable (File)	Description	Data Type
MAIL_USERNAME (app.py / .env)	Email address used to send contact form messages.	string
MAIL_PASSWORD (app.py / .env)	App-specific password for SMTP server authentication.	string
curiosidadIndex (app.js)	Tracks the current index of the active curiosity item in the carousel.	integer
timelineObserver (app.js)	IntersectionObserver instance that triggers the fade-in animation when a timeline item enters the viewport.	IntersectionObserver
formData (app.js)	FormData object containing the user's name, email, and message captured from the HTML form.	FormData
## 🧪 How to Run the Project

  Ensure your .env file is configured with your email credentials.
  Open your terminal in the project root directory.
  Run the Flask application:

python app.py

  Open your web browser and navigate to: http://127.0.0.1:5000

The website will be served locally.

## 🎯 Features & User Interaction

  Interactive Timeline: Users can scroll through a visual history of programming languages, enhanced with CSS animations.
  Downloadable Resources: The portfolio section allows users to preview and download PDFs directly from the browser.
  Contact Form: A fully functional contact form that sends messages directly to the administrator's email inbox via SMTP.
  Video Gallery: Embedded YouTube videos for auxiliary learning content.
  Mobile-First Design: The site is fully responsive and adapts to mobile, tablet, and desktop screen sizes.



