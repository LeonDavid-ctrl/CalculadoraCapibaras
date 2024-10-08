# CalculadoraCapibaras
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Compañia Aerea</title>
    <link rel="stylesheet" href="./Estilos.css">
</head>
<header>
    <ul class="header">
        <li><a href="./Index.html">Registrar</a></li>
        <li><a href="./index2.html">Registros</a></li>
    </ul>
</header>
<body>
    <section class="formularios">
        <form id="avionForm">
            <h1>Ingresar Avion</h1>
            <p><label for="codigoAvion">Código del Avión:</label>
            <input type="text" id="codigoAvion" required></p>
            
            <p><label for="baseAvion">Base:</label>
            <input type="text" id="baseAvion" required></p>
            
            <button type="submit">Agregar Avión</button>
        </form>
        <form id="pilotoForm">
            <h1>Ingresar Piloto</h1>
            <p><label for="codigoPiloto">Código del Piloto:</label>
                <input type="text" id="codigoPiloto" required></p>
            
            <p><label for="nombrePiloto">Nombre:</label>
                <input type="text" id="nombrePiloto" required></p>
    
            <p><label for="horasDeVuelo">Horas De Vuelo:</label>
                <input type="number" id="horasDeVuelo" required></p>
    
            <p><label for="basePiloto">Base:</label>
                <input type="text" id="basePiloto" required></p>
            
            <button type="submit">Agregar Piloto</button>
        </form>
        <form id="miembroForm"> <!-- Corregido el ID aquí -->
            <h1>Ingresar Miembro</h1>
            <p><label for="codigoMiembros">Código del miembro:</label>
                <input type="text" id="codigoMiembro" required></p>
            
            <p><label for="nombreMiembro">Nombre:</label>
                <input type="text" id="nombreMiembro" required></p>
    
            <p><label for="baseMiembro">Base:</label>
                <input type="text" id="baseMiembro" required></p> 
            
            <button type="submit">Agregar Miembro</button>
        </form>
    </section>
    
    <script>
        document.getElementById('avionForm').addEventListener('submit', function(e) {
            e.preventDefault();
            const codigoAvion = document.getElementById('codigoAvion').value;
            const baseAvion = document.getElementById('baseAvion').value;

            const aviones = JSON.parse(localStorage.getItem('aviones')) || [];
            aviones.push({ codigoAvion, baseAvion });
            localStorage.setItem('aviones', JSON.stringify(aviones));

            this.reset(); // Limpiar el formulario
        });

        document.getElementById('pilotoForm').addEventListener('submit', function(e) {
            e.preventDefault();
            const codigoPiloto = document.getElementById('codigoPiloto').value;
            const nombrePiloto = document.getElementById('nombrePiloto').value;
            const horasDeVuelo = document.getElementById('horasDeVuelo').value;
            const basePiloto = document.getElementById('basePiloto').value;

            const pilotos = JSON.parse(localStorage.getItem('pilotos')) || [];
            pilotos.push({ codigoPiloto, nombrePiloto, horasDeVuelo, basePiloto });
            localStorage.setItem('pilotos', JSON.stringify(pilotos));

            this.reset(); // Limpiar el formulario
        });

        document.getElementById('miembroForm').addEventListener('submit', function(e) {
            e.preventDefault();
            const codigoMiembro = document.getElementById('codigoMiembro').value;
            const nombreMiembro = document.getElementById('nombreMiembro').value;
            const baseMiembro = document.getElementById('baseMiembro').value;

            const miembros = JSON.parse(localStorage.getItem('miembros')) || [];
            miembros.push({ codigoMiembro, nombreMiembro, baseMiembro });
            localStorage.setItem('miembros', JSON.stringify(miembros));

            this.reset(); // Limpiar el formulario
        });
    </script>
</body>
<footer>
    <p>© 2021 Compañia Aerea. Todos los derechos reservados.</p>
    <ul class="social-media">
        <li><a href="#"><img src="img/facebook.png" alt="Facebook"></a></li>
        <li><a href="#"><img src="img/twitter.png" alt="Twitter"></a></li>
        <li><a href="#"><img src="img/instagram.png" alt="Instagram"></a></li>
    </ul>
    <ul class="menu-footer">
        <li><a href="#">Home</a></li>
        <li><a href="#">About</a></li>
        <li><a href="#">Services</a></li>
        <li><a href="#">Contact</a></li>
    </ul>
    <p>Email: support@example.com</p>
</footer>
</html>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Registros</title>
    <link rel="stylesheet" href="./Estilos.css">
</head>
<header>
    <ul class="header">
        <li><a href="./Index.html">Registrar</a></li>
        <li><a href="./index2.html">Registros</a></li>
    </ul>
</header>
<body>
    
<table id="tablaAviones">
    <h1>Aviones</h1>
    <tr>
        <th>CodigoAvion</th>
        <th>Base</th>
    </tr>
</table>

<table id="tablaPilotos">
    <h1>Pilotos</h1>
    <tr>
        <th>CodigoPiloto</th>
        <th>Nombre</th>
        <th>Horas De Vuelo</th>
        <th>Base</th>
    </tr>
</table>

<table id="tablaMiembros">
    <h1>Miembros</h1>
    <tr>
        <th>CodigoMiembro</th>
        <th>Nombre</th>
        <th>Base</th>
    </tr>
</table>

<script>
    // Cargar Aviones
    const aviones = JSON.parse(localStorage.getItem('aviones')) || [];
    const tableAviones = document.getElementById('tablaAviones');
    aviones.forEach(avion => {
        const row = tableAviones.insertRow(-1);
        row.insertCell(0).innerText = avion.codigoAvion;
        row.insertCell(1).innerText = avion.baseAvion;
    });

    // Cargar Pilotos
    const pilotos = JSON.parse(localStorage.getItem('pilotos')) || [];
    const tablePilotos = document.getElementById('tablaPilotos');
    pilotos.forEach(piloto => {
        const row = tablePilotos.insertRow(-1);
        row.insertCell(0).innerText = piloto.codigoPiloto;
        row.insertCell(1).innerText = piloto.nombrePiloto;
        row.insertCell(2).innerText = piloto.horasDeVuelo;
        row.insertCell(3).innerText = piloto.basePiloto;
    });

    // Cargar Miembros
    const miembros = JSON.parse(localStorage.getItem('miembros')) || [];
    const tableMiembros = document.getElementById('tablaMiembros');
    miembros.forEach(miembro => {
        const row = tableMiembros.insertRow(-1);
        row.insertCell(0).innerText = miembro.codigoMiembro;
        row.insertCell(1).innerText = miembro.nombreMiembro;
        row.insertCell(2).innerText = miembro.baseMiembro;
    });
</script>
    
</body>
</html>
