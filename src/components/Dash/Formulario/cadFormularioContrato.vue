<template>
  <div class="q-pa-md" style="max-width: 400px">
    <q-form @submit="onSubmit" @reset="onReset" class="q-gutter-md">
      <q-input
        filled
        v-model="name"
        label="Seu Nome *"
        hint="Nome e Sobrenome"
        lazy-rules
        :rules="[
          (val) => (val && val.length > 0) || 'Por favor, informe seu nome',
        ]"
      />

      <q-input
        filled
        type="number"
        v-model="age"
        label="Sua Idade *"
        lazy-rules
        :rules="[
          (val) =>
            (val !== null && val !== '') || 'Por favor, informe sua idade',
          (val) =>
            (val > 18 && val < 100) || 'Por favor, informe uma idade válida',
        ]"
      />

      <q-toggle v-model="accept" label="Eu aceito os termos" />

      <div>
        <q-btn label="Enviar" type="submit" color="primary" />
        <q-btn
          label="Limpar"
          type="reset"
          color="primary"
          flat
          class="q-ml-sm"
        />
      </div>
    </q-form>
  </div>
</template>

<script>
import { useQuasar } from "quasar";
import { ref } from "vue";

export default {
  name: "cadFormularioContrato",
  setup() {
    const $q = useQuasar();

    const name = ref(null);
    const age = ref(null);
    const accept = ref(false);

    return {
      name,
      age,
      accept,

      onSubmit() {
        if (accept.value !== true) {
          $q.notify({
            color: "red-5",
            textColor: "white",
            icon: "warning",
            message: "You need to accept the license and terms first",
          });
        } else {
          $q.notify({
            color: "green-4",
            textColor: "white",
            icon: "cloud_done",
            message: "Submitted",
          });
        }
      },

      onReset() {
        name.value = null;
        age.value = null;
        accept.value = false;
      },
    };
  },
};
</script>
