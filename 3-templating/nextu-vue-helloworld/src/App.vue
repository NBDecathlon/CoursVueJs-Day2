<template>
  <div id="app">
    <div class="container">
      <h1>Formulaire d'inscription</h1>
      <form @submit.prevent="validateForm">

        <div class="form-row">
          <label for="nom">Nom:</label>
          <input type="text" id="nom" v-model="form.nom" />
          <ErrorForms v-if="errors.nom" :message="errors.nom" />
        </div>

        <div class="form-row">
          <label for="prenom">Prénom:</label>
          <input type="text" id="prenom" v-model="form.prenom" />
          <ErrorForms v-if="errors.prenom" :message="errors.prenom" />
        </div>

        <div class="form-row">
          <label for="email">Email:</label>
          <input type="email" id="email" v-model="form.email" />
          <ErrorForms v-if="errors.email" :message="errors.email" />
        </div>

        <div class="form-row">
          <label>Sexe:</label>
          <div class="radio-group">
            <label>
              <input type="radio" value="Homme" v-model="form.sexe" /> Homme
            </label>
            <label>
              <input type="radio" value="Femme" v-model="form.sexe" /> Femme
            </label>
          </div>
          <ErrorForms v-if="errors.sexe" :message="errors.sexe" />
        </div>

        <div class="form-row">
          <label for="adresse">Adresse:</label>
          <input type="text" id="adresse" v-model="form.adresse" />
          <ErrorForms v-if="errors.adresse" :message="errors.adresse" />
        </div>

        <div class="form-row">
          <label for="codePostal">Code postal:</label>
          <input type="text" id="codePostal" v-model="form.codePostal" />
          <ErrorForms v-if="errors.codePostal" :message="errors.codePostal" />
        </div>

        <div class="form-row">
          <label for="ville">Ville:</label>
          <input type="text" id="ville" v-model="form.ville" />
          <ErrorForms v-if="errors.ville" :message="errors.ville" />
        </div>

        <div class="form-row">
          <label for="institut">Nom de l'institut:</label>
          <input type="text" id="institut" v-model="form.institut" />
          <ErrorForms v-if="errors.institut" :message="errors.institut" />
        </div>

        <div class="buttons">
          <button type="submit" class="submit-btn">Valider</button>
          <button type="button" @click="resetForm" class="reset-btn">Annuler</button>
        </div>
      </form>

      <div v-if="formSubmitted">
        <h2>Données soumises :</h2>
        <div class="fiche">
          <p><strong>Nom :</strong> {{ submittedData.nom }}</p>
          <p><strong>Prénom :</strong> {{ submittedData.prenom }}</p>
          <p><strong>Email :</strong> {{ submittedData.email }}</p>
          <p><strong>Sexe :</strong> {{ submittedData.sexe }}</p>
          <p><strong>Adresse :</strong> {{ submittedData.adresse }}</p>
          <p><strong>Code Postal :</strong> {{ submittedData.codePostal }}</p>
          <p><strong>Ville :</strong> {{ submittedData.ville }}</p>
          <p><strong>Institut :</strong> {{ submittedData.institut }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ErrorForms from './ErrorForms.vue';

export default {
  components: {
    ErrorForms,
  },
  data() {
    return {
      form: {
        nom: '',
        prenom: '',
        email: '',
        sexe: '',
        adresse: '',
        codePostal: '',
        ville: '',
        institut: '',
      },
      errors: {
        nom: null,
        prenom: null,
        email: null,
        sexe: null,
        adresse: null,
        codePostal: null,
        ville: null,
        institut: null,
      },
      formSubmitted: false,
      submittedData: {},
    };
  },
  methods: {
    validateForm() {
      this.errors = {
        nom: null,
        prenom: null,
        email: null,
        sexe: null,
        adresse: null,
        codePostal: null,
        ville: null,
        institut: null,
      };

      let isValid = true;

      if (!this.form.nom) {
        this.errors.nom = 'Le champ Nom est requis.';
        isValid = false;
      }

      if (!this.form.prenom) {
        this.errors.prenom = 'Le champ Prénom est requis.';
        isValid = false;
      }

      const emailRegex = /^[^\\s@]+@[^\\s@]+\\.[a-z]{2,}$/i;
      if (!this.form.email) {
        this.errors.email = 'Le champ Email est requis.';
        isValid = false;
      } else if (!emailRegex.test(this.form.email)) {
        this.errors.email = 'Saisissez un email valide.';
        isValid = false;
      }

      if (!this.form.sexe) {
        this.errors.sexe = 'Veuillez sélectionner un sexe.';
        isValid = false;
      }

      if (!this.form.adresse) {
        this.errors.adresse = 'Le champ Adresse est requis.';
        isValid = false;
      }

      const codePostalRegex = /^[0-9]{10}$/;
      if (!this.form.codePostal) {
        this.errors.codePostal = 'Le champ Code postal est requis.';
        isValid = false;
      } else if (!codePostalRegex.test(this.form.codePostal)) {
        this.errors.codePostal = 'Le Code postal doit être composé de 10 chiffres.';
        isValid = false;
      }

      if (!this.form.ville) {
        this.errors.ville = 'Le champ Ville est requis.';
        isValid = false;
      }

      if (!this.form.institut) {
        this.errors.institut = 'Le champ Institut est requis.';
        isValid = false;
      }

      if (isValid) {
        this.submittedData = { ...this.form };
        this.formSubmitted = true;
        this.resetForm();
      }
    },

    resetForm() {
      this.form = {
        nom: '',
        prenom: '',
        email: '',
        sexe: '',
        adresse: '',
        codePostal: '',
        ville: '',
        institut: '',
      };
      this.errors = {
        nom: null,
        prenom: null,
        email: null,
        sexe: null,
        adresse: null,
        codePostal: null,
        ville: null,
        institut: null,
      };
      this.formSubmitted = false;
    },
  },
};
</script>

<style scoped>
.container {
  max-width: 600px;
  margin: auto;
  padding: 20px;
  border: 1px solid rgba(214, 214, 214, 0.2);
  border-radius: 5px;
  background-color: #f9f9f9;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  box-shadow: 0 4px 8px rgba(214, 214, 214, 0.2);
}

form {
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.form-row {
  display: flex;
  flex-direction: column;
}

label {
  margin-bottom: 5px;
  font-weight: bold;
}

input {
  padding: 10px;
  border-radius: 5px;
  border: 1px solid #ccc;
  font-size: 14px;
}

.radio-group {
  display: flex;
  gap: 15px;
}

.error {
  color: red;
  font-size: 12px;
  margin-top: 5px;
}

.buttons {
  display: flex;
  justify-content: flex-end;
  gap: 10px;
}

button {
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
  font-size: 14px;
}

.submit-btn {
  background-color: green;
  color: white;
  border: none;
}

.submit-btn:hover {
  background-color: darkgreen;
}

.reset-btn {
  background-color: #ccc;
  color: black;
  border: none;
}

.reset-btn:hover {
  background-color: #999;
}

.fiche {
  padding: 10px;
  background-color: #e9ecef;
  border-radius: 5px;
  margin-top: 20px;
}
</style>
