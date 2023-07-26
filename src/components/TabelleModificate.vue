<script>
export default {
  data() {
    return {
      ordineCrescente: true
    }
  },
  props: ['jsonImportatoB'],
  methods: {
    rimuoviRiga(index) {
      this.jsonImportatoB.splice(index, 1);
    },
    ordineNome() {
      if (this.ordineCrescente) {
      this.jsonImportatoB.sort((a, b) => a.nome.localeCompare(b.nome));;  
      this.ordineCrescente = !this.ordineCrescente;
      }      
      else {
      this.jsonImportatoB.sort((a, b) => b.nome.localeCompare(a.nome));;  
      this.ordineCrescente = !this.ordineCrescente;
      }
    },
    ordineCognome() {
      if (this.ordineCrescente) {
      this.jsonImportatoB.sort((a, b) => a.cognome.localeCompare(b.cognome));;  
      this.ordineCrescente = !this.ordineCrescente;
      }      
      else {
      this.jsonImportatoB.sort((a, b) => b.cognome.localeCompare(a.cognome));;  
      this.ordineCrescente = !this.ordineCrescente;
      }
    },
    ordineTelefono() {
      if (this.ordineCrescente) {
      this.jsonImportatoB.sort((a, b) => a.telefono - b.telefono);;  
      this.ordineCrescente = !this.ordineCrescente;
      }      
      else {
      this.jsonImportatoB.sort((a, b) => b.telefono - a.telefono);;  
      this.ordineCrescente = !this.ordineCrescente;
      }
    },
  },
  computed: {
     // Per ciascun elemento, creiamo un nuovo oggetto con tutte le proprietà originali
     /* Utilizziamo l'operatore di propagazione per copiare tutte le proprietà originali
    L'operatore di propagazione (...elemento) viene utilizzato qui per copiare tutte le proprietà 
    di un oggetto elemento all'interno di un nuovo oggetto. In altre parole, stiamo creando una 
    copia dell'oggetto elemento in modo da mantenerne tutte le proprietà e i valori originali.
        */ 
    arrayInMaiuscolo() {
    const arrayMaiuscolo = this.jsonImportatoB.map(function(elemento) { // Utilizziamo il metodo map() per iterare attraverso gli elementi dell'array jsonImportatoB   
    return {
      ...elemento, // La proprietà "numero di telefono" rimarrà inalterata poiché non viene modificata qui
      nome: elemento.nome.toUpperCase(), // Convertiamo il valore della proprietà "nome" in maiuscolo
      cognome: elemento.cognome.toUpperCase(), // Convertiamo il valore della proprietà "cognome" in maiuscolo
    };
  });
  // Restituiamo l'array con i valori "nome" e "cognome" convertiti in maiuscolo
  return arrayMaiuscolo;
},
  }
}
</script>

<template>
  <h2>Lista VIP</h2>

  <div class="table-container">
      <table id="strumenti-table">
        <thead>
          <tr v-if="jsonImportatoB.length > 0">
            <th class="nome" @click="ordineNome">Nome</th>
            <th class="cognome" @click="ordineCognome">Cognome</th>
            <th class="telefono" @click="ordineTelefono">Telefono</th> 
            <th></th>
          </tr>
        </thead>
        <tbody v-if="jsonImportatoB.length > 0">
          <tr v-for="(item, index) in arrayInMaiuscolo" :key="index">
            <td>{{ item.nome }}</td>
            <td>{{ item.cognome }}</td>
            <td>{{ item.telefono }}</td>
            <td>
              <button @click="rimuoviRiga(index)">❌</button>
            </td>
          </tr>
          </tbody>
      </table>
  </div>

</template>

<style>
h2 {
  font-family: 'Pirata One', cursive;
  text-align: center;
  color: black;
  font-size: 30px;
}

  /* Colori */
  :root {
    --primary-color: rgba(30, 58, 92, 0.75);
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
    background-color: #f2f2f27f;
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
