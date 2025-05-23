# MWAD-EX_03-To-Do-List-using-JavaScript
## Date: 29/4/2025
# Name : Thirisha A
# Reg no: 212223040228

## AIM
To create a To-do Application with all features using JavaScript.

## ALGORITHM
### STEP 1
Build the HTML structure (index.html).

### STEP 2
Style the App (style.css).

### STEP 3
Plan the features the To-Do App should have.

### STEP 4
Create a To-do application using Javascript.

### STEP 5
Add functionalities.

### STEP 6
Test the App.

### STEP 7
Open the HTML file in a browser to check layout and functionality.

### STEP 8
Fix styling issues and refine content placement.

### STEP 9
Deploy the website.

### STEP 10
Upload to GitHub Pages for free hosting.

## PROGRAM
# index.html:
```

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Smart Reminder App</title>
  <style>

    header {
      text-align: center;
      padding: 1rem;
      background-color: #4b79a1;
      color: white;
      box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    }
    body {
  margin: 0;
  font-family: 'Segoe UI', sans-serif;
  background: linear-gradient(to right, #eef2f3, #8e9eab);
  color: #333;
  display: flex;
  flex-direction: column;
  min-height: 100vh; /* Ensures the body takes full viewport height */
}

footer {
  text-align: center;
  padding: 1rem;
  background-color: #4b79a1;
  color: white;
  margin-top: auto; /* Pushes the footer to the bottom */
}

    .container {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 2rem;
      padding: 2rem;
    }

    .left-panel, .right-panel {
      background: white;
      border-radius: 10px;
      box-shadow: 0 4px 20px rgba(0,0,0,0.1);
      padding: 1.5rem;
      display: flex;
      flex-direction: column;
    }

    h2 {
      border-bottom: 2px solid #4b79a1;
      padding-bottom: 0.5rem;
      margin-bottom: 1rem;
    }

    input, textarea, button {
      width: 100%;
      padding: 0.5rem;
      margin: 0.5rem 0;
      border-radius: 5px;
      border: 1px solid #ccc;
    }

    button {
      background: #4b79a1;
      color: white;
      font-weight: bold;
      cursor: pointer;
      border: none;
      transition: background 0.3s;
    }

    button:hover {
      background: #283e51;
    }

    .reminder {
      padding: 1rem;
      margin: 0.5rem 0;
      background-color: #f1f1f1;
      border-left: 5px solid #4b79a1;
      border-radius: 5px;
    }

    .reminder-actions {
      margin-top: 0.5rem;
      display: flex;
      gap: 0.5rem;
    }

    .reminder-actions button {
      flex: 1;
      font-size: 0.8rem;
    }

    .upcoming-reminders {
      margin-top: 2rem;
    }

  </style>
</head>
<body>
  <header>
    <h1>Smart Reminder App</h1>
  </header>

  <div class="container">
    <!-- Reminder Form and Upcoming -->
    <div class="left-panel">
      <h2>Add Reminder</h2>
      <input type="text" id="title" placeholder="Reminder Title">
      <input type="datetime-local" id="datetime">
      <textarea id="description" placeholder="Reminder Details"></textarea>
      <button onclick="addReminder()">Add Reminder</button>

      <div class="upcoming-reminders">
        <h2>Upcoming Reminders</h2>
        <div id="upcomingReminders"></div>
      </div>
    </div>

    <!-- Past Reminders -->
    <div class="right-panel">
      <h2>Past Reminders</h2>
      <div id="pastReminders"></div>
    </div>
  </div>

  <footer>
    Created by Thirisha 💡
  </footer>

  <script>
    function addReminder() {
      const title = document.getElementById("title").value;
      const datetime = document.getElementById("datetime").value;
      const description = document.getElementById("description").value;

      if (!title || !datetime || !description) {
        alert("Please fill in all fields.");
        return;
      }

      const reminder = {
        title,
        datetime,
        description,
        completed: false
      };

      const reminders = JSON.parse(localStorage.getItem("reminders")) || [];
      reminders.push(reminder);
      localStorage.setItem("reminders", JSON.stringify(reminders));

      displayReminders();

      document.getElementById("title").value = "";
      document.getElementById("datetime").value = "";
      document.getElementById("description").value = "";
    }

    function deleteReminder(index) {
      const reminders = JSON.parse(localStorage.getItem("reminders")) || [];
      reminders.splice(index, 1);
      localStorage.setItem("reminders", JSON.stringify(reminders));
      displayReminders();
    }

    function markCompleted(index) {
      const reminders = JSON.parse(localStorage.getItem("reminders")) || [];
      reminders[index].completed = true;
      localStorage.setItem("reminders", JSON.stringify(reminders));
      displayReminders();
    }

    function displayReminders() {
      const reminders = JSON.parse(localStorage.getItem("reminders")) || [];
      const now = new Date();

      const pastReminders = document.getElementById("pastReminders");
      const upcomingReminders = document.getElementById("upcomingReminders");

      pastReminders.innerHTML = "";
      upcomingReminders.innerHTML = "";

      reminders.forEach((reminder, index) => {
        const reminderDate = new Date(reminder.datetime);
        const div = document.createElement("div");
        div.classList.add("reminder");
        div.innerHTML = `
          <strong>${reminder.completed ? "✅ " : ""}${reminder.title}</strong><br>
          <small>${reminderDate.toLocaleString()}</small>
          <p>${reminder.description}</p>
          <div class="reminder-actions">
            <button onclick="deleteReminder(${index})">Delete</button>
            ${!reminder.completed ? `<button onclick="markCompleted(${index})">Mark Completed</button>` : ""}
          </div>
        `;

        if (reminderDate < now) {
          pastReminders.appendChild(div);
        } else {
          upcomingReminders.appendChild(div);
        }
      });
    }

    window.onload = displayReminders;
  </script>
</body>
</html>
```

## OUTPUT

![Screenshot (82)](https://github.com/user-attachments/assets/3b81f973-7a9e-4c57-a2f9-d0ecc4c3cde4)

![Screenshot (83)](https://github.com/user-attachments/assets/89ec5612-4c9c-47f5-a476-240d15ee4d56)

## RESULT
The program for creating To-do list using JavaScript is executed successfully.
