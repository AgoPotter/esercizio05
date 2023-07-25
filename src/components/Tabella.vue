<script>
export default {
  props: {
    jsonImportato: {
      type: Object,
    }
  }
};
</script>

<template>
  <h2>Lista clienti</h2>

  <div class="table-container">
      <table id="strumenti-table">
        <thead>
          <tr v-if="jsonImportato.length > 0">
            <th class="nome">Nome</th>
            <th class="cognome">Cognome</th>
            <th class="telefono">Telefono</th> 
            <th></th>
          </tr>
        </thead>
        <tbody v-if="jsonImportato.length > 0">
          <tr v-for="(item, index) in jsonImportato" :key="index">
            <td>{{ item.nome }}</td>
            <td>{{ item.cognome }}</td>
            <td>{{ item.telefono }}</td>
            <td>
              <button>❌</button>
            </td>
          </tr>
          </tbody>
      </table>
  </div>

</template>

<style>
  /* Colori */
  :root {
    --primary-color: #1e3a5c;
    --secondary-color: #4a90e2;
  }

  /* Stile della tabella */
  .table-container {
    width: 100%;
    overflow-x: auto;
    border: 2px solid var(--primary-color);
    border-radius: 8px;
  }

  #strumenti-table {
    width: 100%;
    border-collapse: collapse;
    table-layout: fixed;
  }

  /* Stile dell'intestazione della tabella */
  #strumenti-table thead {
    background-color: var(--primary-color);
    color: antiquewhite;
  }

  #strumenti-table td {
    padding: 10px;
    text-align: left;
    font-size: 25px; /* Modifica la grandezza del font desiderata */
  }

  #strumenti-table th {
    padding: 10px;
    text-align: left;
    font-size: 25px; /* Modifica la grandezza del font desiderata */
  }

  /* Stile delle righe della tabella */
  #strumenti-table tbody tr:nth-child(even) {
    background-color: #f2f2f2;
  }

  #strumenti-table tbody td {
    padding: 10px;
    text-align: left;
  }

  /* Stile del bottone */
  #strumenti-table tbody button {
    background-color: var(--secondary-color);
    color: antiquewhite;
    border: none;
    padding: 6px 10px;
    border-radius: 4px;
    cursor: pointer;
    font-size: 14px;
  }

  #strumenti-table tbody button:hover {
    background-color: #2f6cb7;
  }

  #strumenti-table th:hover {
    background-color: var(--secondary-color);
    color: antiquewhite;
    cursor: pointer;
  }
</style>
