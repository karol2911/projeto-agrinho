<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AgroEdu Paraná</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>AgroEdu Paraná</h1>
        <p>Turismo e Educação Rural no Paraná</p>
    </header>

    <main>
        <section id="add-farm">
            <h2>Adicionar Fazenda</h2>
            <input type="text" id="farm-name" placeholder="Nome da fazenda">
            <input type="text" id="farm-location" placeholder="Localização">
            <input type="text" id="farm-activities" placeholder="Atividades (separadas por vírgula)">
            <button onclick="addFarm()">Adicionar Fazenda</button>
        </section>

        <section id="filter-farm">
            <h2>Filtrar por Atividade</h2>
            <input type="text" id="filter-activity" placeholder="Digite uma atividade">
            <button onclick="filterFarms()">Filtrar</button>
        </section>

        <section id="farm-list">
            <h2>Lista de Fazendas</h2>
            <ul id="farms"></ul>
        </section>
    </main>

    <footer>
        <p>AgroEdu Paraná &copy; 2026</p>
    </footer>body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #f9f9f9;
    color: #333;
}

header {
    background-color: #4CAF50;
    color: white;
    text-align: center;
    padding: 20px 0;
}

main {
    padding: 20px;
    max-width: 800px;
    margin: auto;
}

section {
    margin-bottom: 30px;
    background-color: #fff;
    padding: 15px;
    border-radius: 8px;
    box-shadow: 0px 2px 5px rgba(0,0,0,0.1);
}

input {
    padding: 8px;
    margin-right: 10px;
    margin-bottom: 10px;
    width: 200px;
}

button {
    padding: 8px 12px;
    background-color: #4CAF50;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

button:hover {
    background-color: #45a049;
}

ul {
    list-style-type: none;
    padding-left: 0;
}

li {let farms = [
    {
        name: "Fazenda Primavera",
        location: "Curitiba",
        activities: ["colheita de frutas", "passeio a cavalo"]
    },
    {
        name: "Fazenda São José",
        location: "Londrina",
        activities: ["workshop de agroecologia", "observação de aves"]
    }
];

function displayFarms(list = farms) {
    const farmList = document.getElementById("farms");
    farmList.innerHTML = "";
    if(list.length === 0){
        farmList.innerHTML = "<li>Nenhuma fazenda encontrada.</li>";
        return;
    }
    list.forEach(farm => {
        const li = document.createElement("li");
        li.innerHTML = `<strong>${farm.name}</strong> - ${farm.location}<br>Atividades: ${farm.activities.join(", ")}`;
        farmList.appendChild(li);
    });
}

function addFarm() {
    const name = document.getElementById("farm-name").value.trim();
    const location = document.getElementById("farm-location").value.trim();
    const activities = document.getElementById("farm-activities").value.trim().split(",").map(a => a.trim());

    if(!name || !location || activities.length === 0 || activities[0] === ""){
        alert("Por favor, preencha todos os campos corretamente.");
        return;
    }

    farms.push({name, location, activities});
    displayFarms();
    document.getElementById("farm-name").value = "";
    document.getElementById("farm-location").value = "";
    document.getElementById("farm-activities").value = "";
}

function filterFarms() {
    const interest = document.getElementById("filter-activity").value.trim().toLowerCase();
    const filtered = farms.filter(farm => farm.activities.some(a => a.toLowerCase().includes(interest)));
    displayFarms(filtered);
}

// Inicializa a lista
displayFarms();
    margin-bottom: 10px;
    padding: 8px;
    background-color: #e8f5e9;
    border-radius: 5px;
}


    <script src="script.js"></script>
</body>
</html>
