<!DOCTYPE html>
<html>
<head>
    <title>Caesar Cipher Encryption/Decryption</title>
    <style>body {
        font-family: Arial, sans-serif;
        text-align: center;
        margin: 40px;
        background-color: #f0f0f0;
        
       
      }
      
      h1 {
        font-size: 36px;
        color: #333;
        margin-bottom: 30px;
      }
      
      p {
        font-size: 18px;
        margin-bottom: 10px;
      }
      
      .container {
        max-width: 600px;
        margin: 0 auto;
        padding: 20px;
        background-color: #fff;
        border-radius: 5px;
        box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        
      }
      
      .form-control {
        width: 100%;
        padding: 10px;
        border: 1px solid #ccc;
        border-radius: 3px;
        margin-bottom: 20px;
      }
      
      .button-group {
        display: flex;
        justify-content: center;
        margin-bottom: 20px;
      }
      
      .btn {
        padding: 15px 30px;
        font-size: 16px;
        font-weight: bold;
        color: #fff;
        background-color: #4CAF50;
        border: none;
        border-radius: 5px;
        cursor: pointer;
        margin-right: 10px;
      }
      
      .btn-primary {
        background-color: #4CAF50;
      }
      
      .btn-secondary {
        background-color: #607D8B;
      }
      
      .btn-success {
        background-color: #008000;
      }
      
      .btn:hover {
        background-color: #3e8e41;
      }
      
      .output-label {
        margin-bottom: 10px;
      }</style>
</head>
<body>
    <div class="container">
        <h1>Encrypt/Decryption</h1>
        <p>Enter the text to Encrypt or Decrypt:</p>
        <input type="text" id="input-text" class="form-control">
        <p>Enter the key:</p>
        <input type="number" id="shift-amount" class="form-control">
        <div class="button-group">
            <button class="btn btn-primary" onclick="encrypt()">Encrypt</button>
            <button class="btn btn-secondary" onclick="decrypt()">Decrypt</button>
        </div>
        <p class="output-label">PLAIN TEXT:</p>
        <input type="text" id="output-text" class="form-control" readonly>
        <button class="btn btn-success" onclick="reset()">RESET</button>
    </div>
    <script>function encrypt() {
        const inputText = document.getElementById("input-text").value;
        const shiftAmount = parseInt(document.getElementById("shift-amount").value);
        const outputText = caesarCipher(inputText, shiftAmount, true);
        document.getElementById("output-text").value = outputText;
      }
      
      function decrypt() {
        const inputText = document.getElementById("input-text").value;
        const shiftAmount = parseInt(document.getElementById("shift-amount").value);
        const outputText = caesarCipher(inputText, shiftAmount, false);
        document.getElementById("output-text").value = outputText;
      }
      
      function reset() {
        document.getElementById("input-text").value = "";
        document.getElementById("shift-amount").value = "";
        document.getElementById("output-text").value = "";
      }
      
      function caesarCipher(text, shift, encrypt) {
        let result = "";
        for (let i = 0; i < text.length; i++) {
            let char = text.charCodeAt(i);
            if (char >= 65 && char <= 90) { // Uppercase letters
                char = (char + (encrypt ? shift : -shift) - 65) % 26 + 65;
            } else if (char >= 97 && char <= 122) { // Lowercase letters
                char = (char + (encrypt ? shift : -shift) - 97) % 26 + 97;
            }
            result += String.fromCharCode(char);
        }
        return result;
      }</script>
</body>
</html>
