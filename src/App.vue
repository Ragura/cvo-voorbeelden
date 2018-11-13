<template>
  <div id="app">
    <cvo-dropdown-basic :keuzes="namen" @selected="selectedNaam = $event"/>
    <hr>
    <cvo-dropdown-advanced :keuzes="dieren" v-model="selectedDier"/>
    Geselecteerd dier is: {{ selectedDier }}
  </div>
</template>

<script>
import CvoDropdownBasic from './components/CvoDropdownBasic.vue';
import CvoDropdownAdvanced from './components/CvoDropdownAdvanced.vue';

export default {
  // @selected="selectedDier = $event"
  name: 'app',
  data() {
    return {
      dieren: [
        "Hond",
        "Kat",
        "Parkiet",
        "Hamster"
      ],
      namen: [
        "Frank",
        "Veerle",
        "Rita",
        "Daniel"
      ],
      selectedDier: "",
      selectedNaam: ""
    }
  },
  components: {
    CvoDropdownBasic,
    CvoDropdownAdvanced
  }
}
</script>

<style>

</style>
