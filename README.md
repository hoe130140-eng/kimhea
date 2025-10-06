<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>금액 계산기</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      padding: 30px;
      background-color: #f5f5f5;
    }
    h1 {
      margin-bottom: 20px;
    }
    .input-row {
      margin: 10px 0;
    }
    input[type="number"] {
      font-size: 24px;
      width: 200px;
      padding: 10px;
      text-align: right;
    }
    .result {
      margin-top: 30px;
      font-size: 32px;
      font-weight: bold;
    }
    button {
      margin-top: 20px;
      padding: 15px 30px;
      font-size: 20px;
      cursor: pointer;
    }
  </style>
</head>
<body>

  <h1>금액 계산기</h1>

  <div class="input-row">
    5,000원: <input type="number" id="won5000" onkeydown="nextInput(event, 'won1000')">
  </div>
  <div class="input-row">
    1,000원: <input type="number" id="won1000" onkeydown="nextInput(event, 'won500')">
  </div>
  <div class="input-row">
    500원: <input type="number" id="won500" onkeydown="nextInput(event, 'won100')">
  </div>
  <div class="input-row">
    100원: <input type="number" id="won100" onkeydown="nextInput(event, 'won50')">
  </div>
  <div class="input-row">
    50원: <input type="number" id="won50" onkeydown="nextInput(event, 'won10')">
  </div>
  <div class="input-row">
    10원: <input type="number" id="won10" onkeydown="nextInput(event, 'calculateButton')">
  </div>

  <button id="calculateButton" onclick="calculateTotal()">합계 계산</button>
  <div class="result" id="totalResult">총 합계: 0 원</div>
  <button onclick="clearAll()">클리어</button>

  <script>
    function nextInput(event, nextId) {
      if (event.key === 'Enter') {
        event.preventDefault();
        document.getElementById(nextId).focus();
      }
    }

    function calculateTotal() {
      const won5000 = parseInt(document.getElementById('won5000').value) || 0;
      const won1000 = parseInt(document.getElementById('won1000').value) || 0;
      const won500  = parseInt(document.getElementById('won500').value)  || 0;
      const won100  = parseInt(document.getElementById('won100').value)  || 0;
      const won50   = parseInt(document.getElementById('won50').value)   || 0;
      const won10   = parseInt(document.getElementById('won10').value)   || 0;

      const total = (won5000 * 5000) + (won1000 * 1000) + (won500 * 500) +
                    (won100 * 100) + (won50 * 50) + (won10 * 10);

      document.getElementById('totalResult').innerText = `총 합계: ${total.toLocaleString()} 원`;
    }

    function clearAll() {
      const ids = ['won5000', 'won1000', 'won500', 'won100', 'won50', 'won10'];
      ids.forEach(id => document.getElementById(id).value = '');
      document.getElementById('totalResult').innerText = '총 합계: 0 원';
      document.getElementById('won5000').focus();
    }
  </script>

</body>
</html>
