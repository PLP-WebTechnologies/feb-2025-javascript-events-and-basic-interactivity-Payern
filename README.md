# feb-2025-avasjcript-events-and-basic-interactivity

 1. HTML File (`index.html`)
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Webpage</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        #message {
            color: green;
        }
        .error {
            color: red;
        }
        .hidden {
            display: none;
        }
    </style>
</head>
<body>
    <h1>Interactive Webpage</h1>

    <!-- Form Section -->
    <section>
        <h2>Form with Validation</h2>
        <form id="myForm">
            <label for="name">Name:</label>
            <input type="text" id="name" name="name" required>
            <br><br>
            <label for="email">Email:</label>
            <input type="email" id="email" name="email" required>
            <br><br>
            <button type="submit">Submit</button>
        </form>
        <p id="message" class="hidden">Form submitted successfully!</p>
        <p id="formError" class="error hidden">Please fill in all fields correctly.</p>
    </section>

    <hr>

    <!-- Interactive Button Section -->
    <section>
        <h2>Interactive Elements</h2>
        <button id="changeColorBtn">Change Background Color</button>
        <p id="colorText">Click the button to change the background color of this page.</p>
    </section>

    <script src="script.js"></script>
</body>
</html>
```

---

 2. JavaScript File (`script.js`)
```
// Form Validation
const form = document.getElementById("myForm");
const successMessage = document.getElementById("message");
const errorMessage = document.getElementById("formError");

form.addEventListener("submit", function(event) {
    const name = document.getElementById("name").value.trim();
    const email = document.getElementById("email").value.trim();

    if (name === "" || email === "") {
        // Prevent form submission if fields are empty
        event.preventDefault();
        successMessage.classList.add("hidden");
        errorMessage.classList.remove("hidden");
    } else {
        errorMessage.classList.add("hidden");
        successMessage.classList.remove("hidden");
    }
});

// Interactive Button: Change Background Color
const changeColorBtn = document.getElementById("changeColorBtn");
const colors = ["#f4a261", "#2a9d8f", "#e76f51", "#264653", "#457b9d"];

changeColorBtn.addEventListener("click", function() {
    const randomColor = colors[Math.floor(Math.random() * colors.length)];
    document.body.style.backgroundColor = randomColor;
});

