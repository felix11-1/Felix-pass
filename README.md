<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Felix Pass - Password Generator</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <div class="container">
    <h1>Felix Pass</h1>
    <p>Create strong and secure passwords effortlessly!</p>
    <div class="generator">
      <label for="length">Password Length:</label>
      <input type="number" id="length" min="8" max="64" value="16">
      <div class="options">
        <label><input type="checkbox" id="uppercase" checked> Uppercase</label>
        <label><input type="checkbox" id="lowercase" checked> Lowercase</label>
        <label><input type="checkbox" id="numbers" checked> Numbers</label>
        <label><input type="checkbox" id="symbols"> Symbols</label>
      </div>
      <button id="generate">Generate Password</button>
      <input type="text" id="password" readonly>
      <button id="copy">Copy to Clipboard</button>
    </div>
  </div>
  <script src="script.js"></script>
</body>
</html>

HTML (index.html)
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Felix Pass - Password Generator</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <div class="container">
    <h1>Felix Pass</h1>
    <p>Create strong and secure passwords effortlessly!</p>
    <div class="generator">
      <label for="length">Password Length:</label>
      <input type="number" id="length" min="8" max="64" value="16">
      <div class="options">
        <label><input type="checkbox" id="uppercase" checked> Uppercase</label>
        <label><input type="checkbox" id="lowercase" checked> Lowercase</label>
        <label><input type="checkbox" id="numbers" checked> Numbers</label>
        <label><input type="checkbox" id="symbols"> Symbols</label>
      </div>
      <button id="generate">Generate Password</button>
      <input type="text" id="password" readonly>
      <button id="copy">Copy to Clipboard</button>
    </div>
  </div>
  <script src="script.js"></script>
</body>
</html>
CSS (styles.css)
body {
  font-family: Arial, sans-serif;
  background-color: #f4f4f4;
  margin: 0;
  padding: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.container {
  text-align: center;
  background: #fff;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
}

h1 {
  color: #333;
}

.generator {
  margin-top: 20px;
}

label {
  font-size: 14px;
  color: #555;
}

input[type="number"],
input[type="text"] {
  width: 100%;
  margin: 10px 0;
  padding: 8px;
  border: 1px solid #ddd;
  border-radius: 4px;
}

button {
  padding: 10px 20px;
  border: none;
  border-radius: 4px;
  background-color: #5cb85c;
  color: white;
  cursor: pointer;
  font-size: 14px;
}

button:hover {
  background-color: #4cae4c;
}

#password {
  font-weight: bold;
  font-size: 16px;
}

document.getElementById("generate").addEventListener("click", generatePassword);
document.getElementById("copy").addEventListener("click", copyToClipboard);

function generatePassword() {
  const length = parseInt(document.getElementById("length").value);
  const includeUppercase = document.getElementById("uppercase").checked;
  const includeLowercase = document.getElementById("lowercase").checked;
  const includeNumbers = document.getElementById("numbers").checked;
  const includeSymbols = document.getElementById("symbols").checked;

  const uppercaseChars = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
  const lowercaseChars = "abcdefghijklmnopqrstuvwxyz";
  const numberChars = "0123456789";
  const symbolChars = "!@#$%^&*()_+[]{}|;:,.<>?";

  let allChars = "";
  if (includeUppercase) allChars += uppercaseChars;
  if (includeLowercase) allChars += lowercaseChars;
  if (includeNumbers) allChars += numberChars;
  if (includeSymbols) allChars += symbolChars;

  if (!allChars) {
    alert("Please select at least one character type!");
    return;
  }

  let password = "";
  for (let i = 0; i < length; i++) {
    password += allChars[Math.floor(Math.random() * allChars.length)];
  }

  document.getElementById("password").value = password;
}

function copyToClipboard() {
  const passwordField = document.getElementById("password");
  passwordField.select();
  document.execCommand("copy");
  alert("Password copied to clipboard!");
}
