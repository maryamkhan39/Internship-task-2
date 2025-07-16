

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Contact Us</title>
  <link rel="stylesheet" href="style.css" />
  <link href="https://fonts.googleapis.com/css2?family=Roboto&display=swap" rel="stylesheet" />
</head>
<body>
  <div class="container">
    <h1>Contact Us</h1>
    <form id="contactForm">
      <div class="form-group">
        <label for="fullName">Full Name *</label>
        <input type="text" id="fullName" name="fullName" />
        <small class="error" id="nameError"></small>
      </div>

      <div class="form-group">
        <label for="email">Email *</label>
        <input type="text" id="email" name="email" />
        <small class="error" id="emailError"></small>
      </div>

      <div class="form-group">
        <label for="message">Message *</label>
        <textarea id="message" name="message"></textarea>
        <small class="error" id="messageError"></small>
      </div>

      <button type="submit">Submit</button>
      <p class="success-message" id="successMessage"></p>
    </form>
  </div>
  <script src="script.js"></script>
</body>
</html>



2️⃣ CSS Styling (style.css)

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Roboto', sans-serif;
  background: #f5f5f5;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}

.container {
  background: #fff;
  padding: 30px;
  max-width: 500px;
  width: 100%;
  border-radius: 8px;
  box-shadow: 0 4px 10px rgba(0,0,0,0.1);
}

h1 {
  text-align: center;
  margin-bottom: 25px;
  color: #333;
}

.form-group {
  margin-bottom: 20px;
}

label {
  display: block;
  margin-bottom: 6px;
  font-weight: bold;
  color: #555;
}

input,
textarea {
  width: 100%;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 14px;
}

button {
  width: 100%;
  padding: 12px;
  background-color: #007BFF;
  color: white;
  font-size: 16px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}

.error {
  color: red;
  font-size: 13px;
  margin-top: 5px;
}

.success-message {
  color: green;
  font-size: 14px;
  margin-top: 15px;
  text-align: center;
}




3️⃣ JavaScript Validation (script.js)

document.getElementById('contactForm').addEventListener('submit', function (e) {
  e.preventDefault();

  let hasError = false;

  // Clear previous messages
  document.getElementById('nameError').textContent = '';
  document.getElementById('emailError').textContent = '';
  document.getElementById('messageError').textContent = '';
  document.getElementById('successMessage').textContent = '';

  const fullName = document.getElementById('fullName').value.trim();
  const email = document.getElementById('email').value.trim();
  const message = document.getElementById('message').value.trim();

  // Name validation
  if (fullName === '') {
    document.getElementById('nameError').textContent = 'Full Name is required.';
    hasError = true;
  }

  // Email validation
  const emailPattern = /^[^ ]+@[^ ]+\.[a-z]{2,3}$/;
  if (email === '') {
    document.getElementById('emailError').textContent = 'Email is required.';
    hasError = true;
  } else if (!emailPattern.test(email)) {
    document.getElementById('emailError').textContent = 'Enter a valid email.';
    hasError = true;
  }

  // Message validation
  if (message === '') {
    document.getElementById('messageError').textContent = 'Message is required.';
    hasError = true;
  }

  if (!hasError) {
    document.getElementById('successMessage').textContent = 'Thank you for contacting us!';
    document.getElementById('contactForm').reset();
  }
})
