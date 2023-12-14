<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BANCA DE CINEMA - AMENIC </title>
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
