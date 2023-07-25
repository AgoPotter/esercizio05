<script>
/* se usi <script setup> non hai bisogno di importare i components.
Tuttavia usando la modalità "setup" non riesce più a leggere il codice JS!
Per questo ho optato per la versione standard. */
import Tabella from './components/Tabella.vue'
import TabelleModificate from './components/TabelleModificate.vue'

export default {
  components: {
    Tabella,
    TabelleModificate,
  },
  data() {
    return {
      nomeDigitato: '',
      cognomeDigitato: '',
      telefonoDigitato: '',
      vipCard: '',
      JSON:[],
      vipJSON:[]
    }
  },
  methods: {
    aggiungiJSON() {
        if (this.nomeDigitato !=='' && this.cognomeDigitato !=='' && this.telefonoDigitato !=='') {
          if (this.vipCard==0) {
          this.JSON.push({
            nome: this.nomeDigitato,
            cognome: this.cognomeDigitato,
            telefono: this.telefonoDigitato,        
          });
        } else if (this.vipCard==1) {
            this.vipJSON.push({
            nome: this.nomeDigitato,
            cognome: this.cognomeDigitato,
            telefono: this.telefonoDigitato,        
          });
        }
          this.nomeDigitato='';
          this.cognomeDigitato='';
          this.telefonoDigitato='';
          this.vipCard='';
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
<body>
  <div class="input">
    <h1>Registrazione nuove cliente</h1>
    <input v-model="nomeDigitato" type="text" placeholder="Nome" id="nome" />
    <input v-model="cognomeDigitato" type="text" placeholder="Cognome" id="cognome" />
    <input v-model="telefonoDigitato" type="text" placeholder="Telefono" id="telefono" />

    <div id="vipCard">
      <label>Vip Card</label>
        <select v-model="vipCard" type="number" id="quantita" name="vipCard">
          <option value="0">No</option>
          <option value="1">Sì</option>
        </select>
    </div>
    <br>
    <button @click="aggiungiJSON()" id="aggiungi">Aggiungi</button>
  </div>
<br>
  <div class="tabelle">
    <div id="tabella">
      <Tabella/>
    </div>
    <div id="tabellaModificata">
      <TabelleModificate/>
    </div>
  </div>

  <footer><a href="https://it.freepik.com/foto-gratuito/ragazza-graziosa-sorridente-felice-che-usa-i-suoi-soldi-del-deposito-della-carta-di-credito-per-lo-shopping-che-tiene-i-sacchetti-con-i-vestiti_33059874.htm#query=shopping&position=3&from_view=search&track=sph">Immagine di benzoix</a> su Freepik</footer>
</body>
</template>

<style scoped>
body {
  background-image: url('sfondo.jpg');
  background-size: cover; 
  background-position: center; 
}

h1 {
  color: antiquewhite;
  font-size: 30px;
}
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

  /* Stile generale per il contenitore dei campi di input e del pulsante */
  .tabelle {
    display: flex;
    flex-direction: row;
    align-items: center;
    background-color: #1e3a5c; /* Sfondo blu scuro */
    padding: 20px;
    border: 2px solid #4a90e2; /* Bordo blu chiaro */
    border-radius: 10px; /* Border radius */

    /* Larghezza massima, puoi regolare il valore in base alle tue esigenze */
    max-width: 1000px;
    margin: 0 auto; /* Per centrare il contenitore */
  }
 
  #tabella {
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: #A9A9A9; /* Sfondo argento scuro */
    padding: 20px;
    border: 2px solid #4a90e2; /* Bordo blu chiaro */
    border-radius: 10px; /* Border radius */

    /* Larghezza massima, puoi regolare il valore in base alle tue esigenze */
    width: 400px;
    margin: 0 auto; /* Per centrare il contenitore */
  }
 
 #tabellaModificata {
   display: flex;
   flex-direction: column;
   align-items: center;
   background-color: #B8860B; /* Sfondo argento scuro */
   padding: 20px;
   border: 2px solid #4a90e2; /* Bordo blu chiaro */
   border-radius: 10px; /* Border radius */

   /* Larghezza massima, puoi regolare il valore in base alle tue esigenze */
   width: 400px;
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

/* Stile per il select */
.input select {
  width: 20%; /* Riempie tutto lo spazio disponibile */
  padding: 10px;
  font-size: 18px; /* Testo grande */
  margin-bottom: 10px;
  border-radius: 5px; /* Border radius */
  border: none;
  background-color: #f1f1f1; /* Colore di sfondo */
  color: #1e3a5c; /* Colore del testo */
}

/* Stile delle opzioni del select */
.input select option {
  background-color: #f1f1f1; /* Colore di sfondo */
  color: #1e3a5c; /* Colore del testo */
}

/* Stile del select al passaggio del mouse (hover) */
.input select:hover {
  background-color: #e6e6e6; /* Colore di sfondo più chiaro al passaggio del mouse */
}

/* Stile del select al momento del focus */
.input select:focus {
  outline: none; /* Rimuove l'outline evidenziato di default al focus */
  box-shadow: 0 0 5px #4a90e2; /* Aggiunge una leggera ombra blu al focus */
}

/* Stile per il div con ID vipCard */
#vipCard {
  display: flex;
  align-items: center;
  background-color: #1e3a5c;
  padding: 5px;
  border: 2px solid #4a90e2;
  border-radius: 10px;
  width: 125px;
  margin: 0 auto;
}

/* Stile per il testo */
#vipCard label {
  flex: 1; /* Il testo occuperà tutto lo spazio disponibile lasciato dal pulsante */
  color: antiquewhite;
  font-size: 20px;
  margin-right: 10px; /* Spazio tra il testo e il pulsante */
}

  /* Stile generale per il footer */
footer {
  background-color: #1e3a5c;
  border: 2px solid #4a90e2;
  border-radius: 10px; /* Puoi regolare il valore per ottenere un angolo più o meno arrotondato */
  opacity: 0.75;
  padding: 20px; /* Puoi regolare il valore per aumentare o diminuire il padding interno del footer */
  color: white; /* Puoi cambiare il colore del testo a tua discrezione */
}

/* Seleziona tutti i link presenti nel footer e cambia il colore del testo quando vengono sovrastati con il mouse */
footer a {
  color: white;
  text-decoration: none; /* Rimuove la sottolineatura dei link */
}

footer a:hover {
  color: #4a90e2; /* Cambia il colore del testo quando il link viene sovrastato con il mouse */
}
</style>

