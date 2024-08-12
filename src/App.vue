<template>
  <div class="container mt-5">
    <h2>Calculatrice</h2>
    <div class="container">
      <form class="form">
        <div class="form-check">
          <input type="radio" class="form-check-input" id="addition" value="addition" v-model="operation">
          <label class="form-check-label" for="addition">Addition</label>
        </div>
        <div class="form-check">
          <input type="radio" class="form-check-input"  id="soustraction" value="soustraction" v-model="operation">
          <label for="soustraction" class="form-check-label">Soustraction</label>
        </div>
        <div class="form-check">
          <input type="radio" id="multiplication" value="multiplication" class="form-check-input"  v-model="operation">
          <label class="form-check-label" for="multiplication">Multiplication</label>
        </div>
        <div class="form-check">
          <input type="radio" class="form-check-input"  id="division" value="division" v-model="operation">
          <label class="form-check-label" for="division">Division</label>
        </div>
      </form>
    </div>

    <div class="form-group">
      <label for="valeur1">Valeur 1</label>
      <input type="number" id="valeur1" v-model="valeur1" class="form-control">
    </div>

    <div class="form-group">
      <label for="valeur2">Valeur 2</label>
      <input type="number" id="valeur2" v-model="valeur2" class="form-control">
    </div>

    <button class="btn btn-primary mt-3" @click="calculer">Calculer</button>

    <Resultat :resultat="resultat"/>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import Resultat from './components/Resultat.vue';

    const operation = ref('');
    const valeur1 = ref(0);
    const valeur2 = ref(0);
    const resultat = ref(null);

    const calculer = () => {
      let res;
      switch (operation.value) {
        case 'addition':
          res = valeur1.value + valeur2.value;
          break;
        case 'soustraction':
          res = valeur1.value - valeur2.value;
          break;
        case 'multiplication':
          res = valeur1.value * valeur2.value;
          break;
        case 'division':
          res = valeur1.value / valeur2.value;
          break;
        default:
          res = 'Opération non valide';
      }
      resultat.value = res;
    };

</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: rgb(220, 255, 210);
  padding: 20px;
  border-radius: 5px;
}
.form{
  display: grid;
  grid-template-columns: repeat(2, auto);
  gap: 10px;
  margin-top: 10px;
  margin-bottom: 10px;
}

</style>
