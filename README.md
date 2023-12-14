<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BANCA DE CINEMA - AMENIC </title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
        }

        .container {
            padding: 20px;
            border-radius: 10px;
            background: #fff;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            margin: 20x;
        }

        img {
            border-radius: 10px; 
            max-width: 100%; 
        }

        h2, h3 {
            color: #000000;
        }

        form {
            margin-top: 20px;
        }

        label, l {
            display: block;
            margin-bottom: 5px;
        }

        input {
            padding: 8px;
            margin-bottom: 10px;
            width: 100%;
            box-sizing: border-box;
            border: 1px solid #ccc;
            border-radius: 4px;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
        }

        th, td {
            border: 1px solid #ddd;
            padding: 12px;
            text-align: left;
        }

        th {
            background-color: #f2f2f2;
        }

        button[type="button"] {
            background-color: #4fa2d9;
            color: white;
            padding: 8px 12px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }

        button[type="button"]:hover {
            background-color: #4fa2d9;
        }
    </style>
</head>
<body>

    <div class="container">
        <img src="Capturar.PNG" width="500" height="300">

        <form id="crudForm">
            <label for="movieTitle">Título do Filme:</label>
            <input type="text" id="movieTitle" required>

            <label for="ticketType">Tipo de Ingresso:</label>
            <select id="ticketType" required>
                <option value="meia">Meia Entrada (R$12)</option>
                <option value="inteira">Inteira (R$24)</option>
            </select>

            <button type="button" onclick="addEntry()">Adicionar</button>
        </form>

        <h3>Lista de Vendas</h3>

        <table id="salesTable">
            <thead>
                <tr>
                    <th>Título do Filme</th>
                    <th>Tipo de Ingresso</th>
                    <th>Preço do Ingresso</th>
                    <th>Ações</th>
                </tr>
            </thead>
            <tbody>
            </tbody>
        </table>
    </div>

    <script>
        function addEntry() {
            var title = document.getElementById('movieTitle').value;
            var ticketTypeElement = document.getElementById('ticketType');
            var ticketType = ticketTypeElement.options[ticketTypeElement.selectedIndex].text;
            var price = ticketType === 'Meia Entrada (R$12)' ? 12 : 24;

            if (title) {
                var table = document.getElementById('salesTable').getElementsByTagName('tbody')[0];
                var newRow = table.insertRow(table.rows.length);

                var cell1 = newRow.insertCell(0);
                var cell2 = newRow.insertCell(1);
                var cell3 = newRow.insertCell(2);
                var cell4 = newRow.insertCell(3);

                cell1.innerHTML = title;
                cell2.innerHTML = ticketType;
                cell3.innerHTML = '$' + price;
                cell4.innerHTML = '<button type="button" onclick="deleteRow(this)">Excluir</button>';
            } else {
                alert('Por favor, preencha todos os campos.');
            }
        }

        function deleteRow(button) {
            var row = button.parentNode.parentNode;
            row.parentNode.removeChild(row);
        }
    </script>

</body>
</html>
