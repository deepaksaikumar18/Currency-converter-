# Currency-converter-
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Currency Converter</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f0f2f5;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }
    .converter {
      background: white;
      padding: 30px;
      border-radius: 10px;
      box-shadow: 0 0 15px rgba(0,0,0,0.1);
      width: 300px;
    }
    .converter h2 {
      text-align: center;
      margin-bottom: 20px;
    }
    .converter input, .converter select, .converter button {
      width: 100%;
      padding: 10px;
      margin: 10px 0;
      font-size: 16px;
    }
    .result {
      text-align: center;
      margin-top: 20px;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <div class="converter">
    <h2>Currency Converter</h2>
    <input type="number" id="amount" placeholder="Enter amount" />
    <select id="fromCurrency">
      <option value="USD">USD</option>
      <option value="EUR">EUR</option>
      <option value="INR">INR</option>
    </select>
    <select id="toCurrency">
      <option value="INR">INR</option>
      <option value="USD">USD</option>
      <option value="EUR">EUR</option>
    </select>
    <button onclick="convertCurrency()">Convert</button>
    <div class="result" id="result"></div>
  </div>

  <script>
    const rates = {
      USD: { INR: 83.1, EUR: 0.92, USD: 1 },
      INR: { USD: 0.012, EUR: 0.011, INR: 1 },
      EUR: { USD: 1.09, INR: 90.5, EUR: 1 }
    };

    function convertCurrency() {
      const amount = parseFloat(document.getElementById("amount").value);
      const from = document.getElementById("fromCurrency").value;
      const to = document.getElementById("toCurrency").value;

      if (isNaN(amount)) {
        document.getElementById("result").innerText = "Please enter a valid amount.";
        return;
      }

      const converted = amount * rates[from][to];
      document.getElementById("result").innerText = `${amount} ${from} = ${converted.toFixed(2)} ${to}`;
    }
  </script>
</body>
</html>
