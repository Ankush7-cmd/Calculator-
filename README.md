# Calculator-
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Advanced Calculator</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f3f4f6;
            margin: 0;
        }
        .calculator {
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
            background-color: #ffffff;
            width: 400px;
        }
        .display {
            background-color: #1f2937;
            color: white;
            padding: 20px;
            text-align: right;
            font-size: 1.5em;
        }
        .buttons {
            display: grid;
            grid-template-columns: repeat(5, 1fr);
        }
        button {
            padding: 15px;
            font-size: 1.2em;
            border: 1px solid #e5e7eb;
            background-color: #f9fafb;
            cursor: pointer;
        }
        button:hover {
            background-color: #e5e7eb;
        }
        button.operator {
            background-color: #60a5fa;
            color: white;
        }
    </style>
</head>
<body>
    <div class="calculator">
        <div class="display" id="display">0</div>
        <div class="buttons">
            <button onclick="clearDisplay()">C</button>
            <button onclick="deleteLast()">DEL</button>
            <button onclick="appendToDisplay('(')">(</button>
            <button onclick="appendToDisplay(')')">)</button>
            <button onclick="appendToDisplay('/')">/</button>

            <button onclick="appendToDisplay('7')">7</button>
            <button onclick="appendToDisplay('8')">8</button>
            <button onclick="appendToDisplay('9')">9</button>
            <button onclick="appendToDisplay('*')">*</button>
            <button onclick="appendToDisplay('^')">^</button>

            <button onclick="appendToDisplay('4')">4</button>
            <button onclick="appendToDisplay('5')">5</button>
            <button onclick="appendToDisplay('6')">6</button>
            <button onclick="appendToDisplay('-')">-</button>
            <button onclick="appendToDisplay('√(')">√</button>

            <button onclick="appendToDisplay('1')">1</button>
            <button onclick="appendToDisplay('2')">2</button>
            <button onclick="appendToDisplay('3')">3</button>
            <button onclick="appendToDisplay('+')">+</button>
            <button onclick="appendToDisplay('π')">π</button>

            <button onclick="appendToDisplay('0')">0</button>
            <button onclick="appendToDisplay('.')">.</button>
            <button onclick="appendToDisplay('sin(')">sin</button>
            <button onclick="appendToDisplay('cos(')">cos</button>
            <button onclick="calculate()">=</button>
        </div>
    </div>

    <script>
        const display = document.getElementById('display');

        function appendToDisplay(value) {
            if (display.innerText === '0') display.innerText = '';
            display.innerText += value;
        }

        function clearDisplay() {
            display.innerText = '0';
        }

        function deleteLast() {
            display.innerText = display.innerText.slice(0, -1);
            if (display.innerText === '') display.innerText = '0';
        }

        function calculate() {
            try {
                let result = display.innerText
                    .replace(/π/g, Math.PI)
                    .replace(/√\(/g, 'Math.sqrt(')
                    .replace(/sin\(/g, 'Math.sin(')
                    .replace(/cos\(/g, 'Math.cos(')
                    .replace(/\^/g, '**');
                display.innerText = eval(result);
            } catch {
                display.innerText = 'Error';
            }
        }
    </script>
</body>
</html>
