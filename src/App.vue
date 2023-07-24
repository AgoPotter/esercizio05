<script>
import Tabella from './components/Tabella.vue'
import TabelleModificate from './components/TabelleModificate.vue'

export default {
  data() {
    return {
      nomeDigitato: '',
      cognomeDigitato: '',
      telefonoDigitato: '',
      JSON:[]
    }
  },
  // components:{Riga},
  methods: {
    aggiungiJSON() {
      if (this.nomeDigitato !==0 && this.cognomeDigitato !=='' && this.telefonoDigitato !=='') {

        this.JSON.push({
          nome: this.nomeDigitato,
          cognome: this.cognomeDigitato,
          telefono: this.telefonoDigitato,        
        });
        this.nomeDigitato='';
        this.cognomeDigitato='';
        this.telefonoDigitato='';
        } else {

        alert("Oh oh... sembra che tu abbia dimenticato di completare tutti i campi.");
      }
    }
  },

  computed: {
  },
}

</script>

<template>
  <div class="input">
    <input v-model="nomeDigitato" type="text" placeholder="Digita il NOME" id="nome" />
    <input v-model="cognomeDigitato" type="text" placeholder="Digita il COGNOME" id="cognome" />
    <input v-model="telefonoDigitato" type="text" placeholder="Digita il TELEGONO" id="telefono" />
    <button @click="aggiungiJSON()" id="aggiungi">Aggiungi</button>
  </div>
  <Tabella/>
  <TabelleModificate/>
</template>

<style scoped>
  /* Stile generale per il contenitore dei campi di input e del pulsante */
  .input {
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: #1e3a5c; /* Sfondo blu scuro */
    padding: 20px;
    border: 2px solid #4a90e2; /* Bordo blu chiaro */
    border-radius: 10px; /* Border radius */

    /* Larghezza massima, puoi regolare il valore in base alle tue esigenze */
    max-width: 400px;
    margin: 0 auto; /* Per centrare il contenitore */
  }

  /* Stile per i campi di input */
  .input input[type="text"] {
    width: 100%; /* Riempiono tutto lo spazio disponibile */
    padding: 10px;
    font-size: 18px; /* Testo grande */
    margin-bottom: 10px;
    border-radius: 5px; /* Border radius per i campi di input */
    border: none;
    background-color: #f1f1f1; /* Colore di sfondo dei campi di input */
  }

  /* Stile per il pulsante */
  .input button {
    padding: 15px 30px;
    font-size: 20px; /* Testo grande */
    border: none;
    background-color: #4a90e2; /* Colore di sfondo blu chiaro */
    color: white; /* Testo bianco */
    border-radius: 5px; /* Border radius per il pulsante */
    cursor: pointer;
  }

  /* Stile del pulsante al passaggio del mouse (hover) */
  .input button:hover {
    background-color: #1857a9; /* Colore di sfondo più scuro al passaggio del mouse */
  }
</style>

