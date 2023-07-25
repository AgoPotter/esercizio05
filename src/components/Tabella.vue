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