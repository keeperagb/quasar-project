<template>
  <q-layout view="hHh lpR fFf" class="bg-grey-1">
    <menu-inicio />
    <q-page-container class="cor">
      <topo-dash-vue />
      <cadFormularioContrato />
    </q-page-container>
  </q-layout>
</template>

<script>
import menuInicio from "./components/Dash/menuInicio.vue";
import topoDashVue from "./components/Dash/topoDash.vue";
import cadFormularioContrato from "./components/Dash/Formulario/cadFormularioContrato.vue";

export default {
  name: "App",
  components: {
    menuInicio,
    topoDashVue,
    cadFormularioContrato,
  },
};
</script>

<style></style>
