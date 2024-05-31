<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Guessing Game</title>
    <link rel="stylesheet" href="style.css">
    <style>
        body {
    font-family: Arial, sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background-color: #f0f0f0;
    margin: 0;
}

.container {
    text-align: center;
    background-color: #fff;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

input[type="number"] {
    padding: 10px;
    font-size: 1em;
    width: 60%;
    margin: 10px 0;
}

button {
    padding: 10px 20px;
    font-size: 1em;
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

button:hover {
    background-color: #0056b3;
}

#message {
    margin-top: 20px;
    font-size: 1.2em;
}

    </style>
    <script>document.addEventListener('DOMContentLoaded', () => {
    const guessInput = document.getElementById('guessInput');
    const guessButton = document.getElementById('guessButton');
    const message = document.getElementById('message');
    
    let randomNumber = Math.floor(Math.random() * 100) + 1;
    let attempts = 0;
    const maxAttempts = 3;

    guessButton.addEventListener('click', () => {
        const userGuess = parseInt(guessInput.value);
        if (isNaN(userGuess) || userGuess < 1 || userGuess > 100) {
            message.textContent = "Please enter a valid number between 1 and 100.";
            return;
        }

        attempts++;
        
        if (userGuess === randomNumber) {
            message.textContent = `Congratulations! You guessed the number in ${attempts} attempts.`;
            guessButton.disabled = true;
        } else if (attempts >= maxAttempts) {
            message.textContent = `Sorry, you've used all your attempts. The number was ${randomNumber}.`;
            guessButton.disabled = true;
        } else {
            if (userGuess < randomNumber) {
                message.textContent = "Too low! Try again.";
            } else {
                message.textContent = "Too high! Try again.";
            }
        }
    });
});
</script>
</head>
<body>
    <div class="container">
        <h1>Guessing Game</h1>
        <p>Guess the number between 1 and 100</p>
        <input type="number" id="guessInput" min="1" max="100" placeholder="Enter your guess" />
        <button id="guessButton">Guess</button>
        <p id="message"></p>
    </div>
    <script src="script.js"></script>
</body>
</html>

