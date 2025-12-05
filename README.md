📄 Registration Form Validation – README

Overview

This project implements a simple, clean, and fully client-side registration form validation system using JavaScript.
The script validates user input for username, email, and password, and displays real-time feedback to the user without reloading the page.

🚀 Features

Executes only after the HTML document is fully loaded (DOMContentLoaded).

Retrieves user input safely using .value.trim().

Validates:

Username length (minimum 3 characters)

Email format (must contain @ and .)

Password length (minimum 8 characters)

Prevents form submission until all inputs meet requirements.

Displays success or error messages dynamically.

📂 Project Structure
project/
│
├── form1.html
├── script.js
|-- style.css
└── README.md

🧩 How It Works
1. DOMContentLoaded Listener

All logic is wrapped inside:

document.addEventListener("DOMContentLoaded", function () {
    // script here...
});


This ensures the form and DOM elements are fully available before the script runs.

2. Form & Feedback Selection

The script selects:

The form (id="registration-form")

The feedback container (id="form-feedback")

const form = document.getElementById("registration-form");
const feedbackDiv = document.getElementById("form-feedback");

3. Form Submission Handling

The form listens for the submit event:

form.addEventListener("submit", function(event) {
    event.preventDefault();
});


This stops the page from reloading so validation can run first.

4. Retrieving & Trimming Inputs
const username = document.getElementById("username").value.trim();
const email    = document.getElementById("email").value.trim();
const password = document.getElementById("password").value.trim();


Trimming removes extra spaces that could cause invalid input.

5. Validation Logic

Two variables are initialized:

let isValid = true;
const messages = [];

Username Validation
if (username.length < 3) {
    isValid = false;
    messages.push("Username must be at least 3 characters long.");
}

Email Validation
if (!email.includes("@") || !email.includes(".")) {
    isValid = false;
    messages.push("Please enter a valid email address.");
}

Password Validation
if (password.length < 8) {
    isValid = false;
    messages.push("Password must be at least 8 characters long.");
}

6. Displaying Feedback

If all inputs are valid:

feedbackDiv.textContent = "Registration successful!";
feedbackDiv.style.color = "#28a745"; // Green


If errors exist:

feedbackDiv.innerHTML = messages.join("<br>");
feedbackDiv.style.color = "#dc3545"; // Red


The feedback box is also made visible:

feedbackDiv.style.display = "block";

✔️ Conclusion

This script provides a lightweight and clear approach to validating form input.
It can easily be extended with additional rules such as confirming passwords, validating phone numbers, or checking for stronger password complexity.
