<template>
    <div v-if="resultat !== null" class="alert alert-info mt-3">
      Résultat : {{ resultat }}
    </div>
  </template>
  
  <script>
  import { defineComponent } from 'vue';
  
  export default defineComponent({
    props: {
      resultat: {
        type: [Number, String],
        default: null
      }
    }
  });
  </script>
  