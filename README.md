# CREDITO-PyS-Motos
FINANCIACIÓN SIN REQUISITOS 
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Simulador de Crédito Personal</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f1f1f1;
      padding: 20px;
    }
    .container {
      max-width: 500px;
      background: white;
      margin: auto;
      padding: 30px;
      border-radius: 10px;
      box-shadow: 0 0 10px #ccc;
    }
    input, select, button {
      width: 100%;
      padding: 10px;
      margin: 10px 0;
    }
    .result {
      background: #e1f5fe;
      padding: 15px;
      border-radius: 5px;
      margin-top: 20px;
    }
  </style>
</head>
<body>
  <div class="container">
    <h2>Simulador de Crédito Personal</h2>

    <label for="amount">Monto del crédito ($):</label>
    <input type="number" id="amount" placeholder="Ej. 10000" />

    <label for="rate">Tasa de interés anual (%):</label>
    <input type="number" id="rate" placeholder="Ej. 12" />

    <label for="term">Plazo (meses):</label>
    <select id="term">
      <option value="8">8 meses</option>
      <option value="12">12 meses</option>
      <option value="18">18 meses</option>
      <option value="24">24 meses</option>
      <option value="36">36 meses</option>
    </select>

    <button onclick="calcularCredito()">Calcular</button>

    <div class="result" id="result" style="display:none;">
      <p><strong>Cuota mensual:</strong> $<span id="cuota"></span></p>
      <p><strong>Total pagado:</strong> $<span id="total"></span></p>
      <p><strong>Total intereses:</strong> $<span id="intereses"></span></p>
    </div>
  </div>

  <script>
    function calcularCredito() {
      const monto = parseFloat(document.getElementById('amount').value);
      const tasaAnual = parseFloat(document.getElementById('rate').value);
      const plazoMeses = parseInt(document.getElementById('term').value);

      if (i
      
