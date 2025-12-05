<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Math Helper Pro</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: #f2f2f2;
            margin: 0;
            padding: 30px;
            text-align: center;
        }
        .box {
            background: white;
            padding: 25px;
            margin: 20px auto;
            width: 380px;
            border-radius: 12px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }
        input {
            padding: 10px;
            margin: 5px;
            width: 140px;
        }
        button {
            padding: 10px 20px;
            margin-top: 10px;
            cursor: pointer;
            border: none;
            background: #007bff;
            color: white;
            border-radius: 6px;
            font-size: 16px;
        }
    </style>
</head>
<body>
    <h1>Math Helper Pro</h1>

    <div class="box">
        <h2>Add / Subtract / Multiply / Divide</h2>
        <input id="a1" type="number" placeholder="Number 1" />
        <br>
        <input id="a2" type="number" placeholder="Number 2" />
        <br>
        <button onclick="calc('add')">Add</button>
        <button onclick="calc('sub')">Subtract</button>
        <button onclick="calc('mul')">Multiply</button>
        <button onclick="calc('div')">Divide</button>
        <h2 id="basicResult"></h2>
    </div>

    <div class="box">
        <h2>LCM & HCF Calculator (Integers Only)</h2>
        <input id="n1" type="number" placeholder="Number 1" />
        <br>
        <input id="n2" type="number" placeholder="Number 2" />
        <br>
        <button onclick="findHCF()">Find HCF</button>
        <button onclick="findLCM()">Find LCM</button>
        <h2 id="lcmhcfResult"></h2>
    </div>

    <script>
        function calc(type) {
            let x = Number(document.getElementById("a1").value);
            let y = Number(document.getElementById("a2").value);

            if (isNaN(x) || isNaN(y)) {
                document.getElementById("basicResult").innerText = "Please enter valid numbers";
                return;
            }

            let result;
            if (type === 'add') result = x + y;
            if (type === 'sub') result = x - y;
            if (type === 'mul') result = x * y;
            if (type === 'div') result = y !== 0 ? x / y : "Cannot divide by zero";

            document.getElementById("basicResult").innerText = "Answer: " + result;
        }

        function gcd(a, b) {
            a = Math.floor(Math.abs(a));
            b = Math.floor(Math.abs(b));
            if (a === 0 || b === 0) return 0;
            while (b) {
                let temp = b;
                b = a % b;
                a = temp;
            }
            return a;
        }

        function findHCF() {
            let a = Number(document.getElementById("n1").value);
            let b = Number(document.getElementById("n2").value);

            if (!Number.isInteger(a) || !Number.isInteger(b) || a <= 0 || b <= 0) {
                document.getElementById("lcmhcfResult").innerText = "Enter positive integers only";
                return;
            }

            document.getElementById("lcmhcfResult").innerText = "HCF: " + gcd(a, b);
        }

        function findLCM() {
            let a = Number(document.getElementById("n1").value);
            let b = Number(document.getElementById("n2").value);

            if (!Number.isInteger(a) || !Number.isInteger(b) || a <= 0 || b <= 0) {
                document.getElementById("lcmhcfResult").innerText = "Enter positive integers only";
                return;
            }

            let lcm = (a * b) / gcd(a, b);
            document.getElementById("lcmhcfResult").innerText = "LCM: " + lcm;
        }
    </script>
</body>
</html> 
