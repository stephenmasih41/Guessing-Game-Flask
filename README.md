# 🎮 Flask Number Guessing Game

A fun and interactive web-based number guessing game built with Flask! Try to guess the secret number between 0 and 9! 🎯


## ✨ Features

- 🎲 Random number generation (0-9)
- 🌐 Web-based interface with Flask
- 🎨 Colorful feedback messages
- 🖼️ Fun GIF animations for each response
- ✅ Input validation to ensure numbers are within range
- 🔄 Dynamic routing for user guesses

## 🎯 How It Works

1. **Start the game** - Visit the home page to see the instructions
2. **Make a guess** - Add your guess to the URL (e.g., `/5`)
3. **Get feedback** - The game tells you if you're too high, too low, or correct!
4. **Keep trying** - Keep guessing until you find the secret number! 🎉


## 🎮 Usage

### Home Page
Navigate to `http://127.0.0.1:5000/` to see the welcome screen with instructions.

### Making a Guess
Add your guess to the URL:
- `http://127.0.0.1:5000/5` - Guess the number 5
- `http://127.0.0.1:5000/7` - Guess the number 7
- `http://127.0.0.1:5000/0` - Guess the number 0

### Possible Responses

| Response | Color | Meaning |
|----------|-------|---------|
| 🟣 **Too high, try again!** | Purple | Your guess is higher than the secret number |
| 🔴 **Too low, try again!** | Red | Your guess is lower than the secret number |
| 🟢 **You found me!** | Green | Correct! You guessed the number! |
| 🟠 **Please choose a number between 0 and 9** | Orange | Your input is outside the valid range |

## 🔧 Code Breakdown

### 📥 Imports
```python
from flask import Flask
import random
```
- **Flask** 🌐: Web framework to create the application
- **random** 🎲: Generates the secret random number

### 🎲 Random Number Generation
```python
random_number = random.randint(0,9)
```
- Generates a random integer between 0 and 9 (inclusive)
- This is the secret number players need to guess!

### ⚙️ Flask Setup
```python
app = Flask(__name__)
```
- Creates the Flask application instance
- `__name__` tells Flask where to find resources

### 🏠 Home Page Route
```python
@app.route("/")
def home():
```
- **Route:** `/` (root URL)
- **Function:** Displays welcome message and instructions
- **Returns:** HTML with heading and GIF

### 🎯 Game Logic Route
```python
@app.route("/<int:userinput>")
def check_number(userinput):
```
- **Route:** `/<int:userinput>` - Accepts any integer in the URL
- **Parameter:** `userinput` - The number guessed by the player
- **Validation:** Checks if the number is between 0-9
- **Comparison Logic:**
  - ✅ **Range Check:** Validates input is 0-9
  - 🔼 **Too High:** `userinput > random_number`
  - 🔽 **Too Low:** `userinput < random_number`
  - 🎯 **Correct:** `userinput == random_number`

### 🏃 Run the Application
```python
if __name__ == "__main__":
    app.run(debug=True)
```
- Starts the Flask development server
- **debug=True** enables:
  - 🔄 Auto-reload on code changes
  - 🐛 Detailed error messages
  - 🛠️ Interactive debugger

## 💻 Technologies Used

- **Python** 🐍 - Programming language
- **Flask** 🌐 - Web framework
- **HTML** 📄 - Content structure
- **Inline CSS** 🎨 - Styling
- **Giphy** 🎬 - GIF animations


## 📝 Notes

- 🔄 The random number is generated when the server starts and stays the same until restart
- 🐛 Debug mode should be turned off in production (`debug=False`)
- 🌐 The game runs on `localhost` by default

