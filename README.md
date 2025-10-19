<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>PyS Motos  - Catálogo y Financiamiento</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      background-color: #f0f8ff;
      color: #333;
    }

    header {
      background-color: #0057B8;
      color: white;
      padding: 20px;
      text-align: center;
    }

    nav {
      background-color: #003f7f;
      display: flex;
      justify-content: center;
      gap: 30px;
      padding: 10px 0;
    }

    nav a {
      color: white;
      text-decoration: none;
      font-weight: bold;
    }

    .filtros {
      padding: 20px;
      background: #e6f2ff;
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 20px;
    }

    .filtros select {
      padding: 10px;
      border-radius: 5px;
      border: 1px solid #ccc;
    }

    .catalogo {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      padding: 20px;
      gap: 20px;
    }

    .moto {
      background: white;
      border: 1px solid #ccc;
      border-radius: 10px;
      width: 300px;
      padding: 15px;
      box-shadow: 0 2px 6px rgba(0,0,0,0.1);
    }

    .moto img {
      width: 100%;
      border-radius: 8px;
    }

    .btn {
      background-color: #0057B8;
      color: white;
      padding: 10px;
      border: none;
      border-radius: 5px;
      text-align: center;
      display: block;
      margin-top: 10px;
      text-decoration: none;
    }

    footer {
      background-color: #003f7f;
      color: white;
      text-align: center;
      padding: 15px;
      margin-top: 40px;
    }
  </style>
</head>
<body>

  <header>
    <h1>Motos</h1>
    <p>Comercialización, Modelos y Financiamiento</p>
  </header>

  <nav>
    <a href="#INICIO">INICIO</a>
    <a href="#CATÁLOGO">CATÁLOGO</a>
    <a href="#Financiamiento">Financiamiento</a>
    <a href="#Contacto">Contacto</a>
  </nav>

  <section class="filtros">
    <select id="marcaFiltro">
      <option value="">Todas las marcas</option>
      <option value="YAMAHA">YAMAHA</option>
      <option value="HONDA">HONDA</option>
      <option value="GILERA">GILERA</option>
      <option value="ZANELLA">ZANELLA</option>
      <option value="MOTOMEL">MOTOMEL</option>
      <option value="CORVEN">CORVEN</option>
      <option value="KELLER">KELLER</option>
      <option value="CERRO">CERRO</option>
      <option value="BRAVA">BRAVA</option>
      <option value="RUOSER">ROUSER</option>
      <option value="HERO">HERO</option>
      <option value="TVS">TVS</option>
    </select>

    <select id="tipoFiltro">
      <option value="">Todos los tipos</option>
      <option value="Deportiva">Deportiva</option>
      <option value="Urbana">Urbana</option>
      <option value="Adventure">Adventure</option>
    </select>

    <select id="precioFiltro">
      <option value="">Todos los precios</option>
      <option value="bajo">Menos de $2.000.000,00</option>
      <option value="medio">$3.000.000,00 - $6.000.000,00</option>
      <option value="alto">Más de $6.000.000,00</option>
    </select>
  </section>

  <section class="catalogo" id="catalogo">
    <!-- Las motos se generarán dinámicamente aquí -->
  </section>

  <section id="financiamiento" style="padding: 30px; text-align: center;">
    <h2>Simulador de Financiamiento</h2>
    <p>Ingresa el valor de la moto y selecciona meses:</p>
    <input type="number" id="monto" placeholder="Valor de la moto" />
    <select id="cuotas">
      <option value="6">6 Meses</option>
      <option value="8">8 Meses</option>
      <option value="12">12 meses</option>
      <option value="18">18 Meses</option>
      <option value="24">24 Meses</option>
    </select>
    <button class="btn" onclick="simular()">Calcular</button>
    <p id="resultado"></p>
  </section>

  <footer id="contacto">
    <p>&copy; 2025 Motos. Todos los derechos reservados.</p>
  </footer>

  <script>
    const motos = [
      {
        nombre: "Yamaha FZ",
        marca: "Yamaha",
        tipo: "Deportiva",
        precio: "$5.890.000,00",
        imagen: "https://via.placeholder.com/300x200?text=Yamaha+FZ"
      },
      {
        nombre: "Honda Tornado 300 L",
        marca: "Honda",
        tipo: "Enduro",
        precio: *$10.890.000,00*,
        imagen: "https://via.placeholder.com/300x200?text=Honda+300L"
      },
      {
        nombre: "Suzuki ax 100",
        marca: "Suzuki",
        tipo: "Cub",
        precio: 2.780.000,00,
        imagen: "https://via.placeholder.com/300x200?text=Suzuki+VStrom+650"
      },
      {
        nombre: "Honda GLH",
        marca: "Honda",
        tipo: "Deportiva",
        precio: 5.920.000,00,
        imagen: "https://via.placeholder.com/300x200?text=Honda+CBR+500R"
      }
    ];

    const catalogo = document.querySelector(".catalogo");

    function mostrarMotos(filtro = {}) {
      catalogo.innerHTML = "";
      const filtradas = motos.filter(moto => {
        return (!filtro.marca || moto.marca === filtro.marca) &&
               (!filtro.tipo || moto.tipo === filtro.tipo) &&
               (!filtro.precio || (
                 filtro.precio === "bajo" && moto.precio < 2.000000 ||
                 filtro.precio === "medio" && moto.precio >= 2.000000 && moto.precio <= 6000000 ||
                 filtro.precio === "alto" && moto.precio > 6000000
               ));
      });

      if (filtradas.length === 0) {
        catalogo.innerHTML = "<p>No se encontraron motos con esos filtros.</p>";
      } else {
        filtradas.forEach(moto => {
          catalogo.innerHTML += `
            <div class="moto">
              <img src="${moto.imagen}" alt="${moto.nombre}">
              <h3>${moto.nombre}</h3>
              <p>Marca: ${moto.marca}</p>
              <p>Tipo: ${moto.tipo}</p>
              <p>Precio: $${moto.precio.toLocaleString()}</p>
              <a href="#financiamiento" class="btn">Ver Financiamiento</a>
            </div>
          `;
        });
      }
    }

    function simular() {
      const monto = parseFloat(document.getElementById("monto").value);
      const cuotas = parseInt(document.getElementById("cuotas").value);
      const tasa = 15.7; // 15% mensual
      if (isNaN(monto)) {
        document.getElementById("resultado").innerText = "Por favor ingresa un monto válido.";
        return;
      }

      const cuotaMensual = (monto * (1 + tasa * cuotas)) / cuotas;
      document.getElementById("resultado").innerText = `Cuota mensual aproximada: $${cuotaMensual.toFixed(2)}`;
    }

    // Eventos de filtros
    document.getElementById("marcaFiltro").addEventListener("change", filtrar);
    document.getElementById("tipoFiltro").addEventListener("change", filtrar);
    document.getElementById("precioFiltro").addEventListener("change", filtrar);

    function filtrar() {
      const marca = document.getElementById("marcaFiltro").value;
      const tipo = document.getElementById("tipoFiltro").value;
      const precio = document.getElementById("precioFiltro").value;
      mostrarMotos({ marca, tipo, precio });
    }

    // Mostrar todas las motos al cargar
    mostrarMotos();
  </script>

</body>
</html>
