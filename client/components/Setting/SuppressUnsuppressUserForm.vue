<script setup lang="ts">
import { useSettingsStore } from "@/stores/settings";
import { ref } from "vue";
let suppressee = ref("");
let unsuppressee = ref("");
const { suppressUser, unsuppressUser } = useSettingsStore();
async function addSuppression() {
  await suppressUser(suppressee.value);
  suppressee.value = "";
}
async function removeSuppression() {
  await unsuppressUser(unsuppressee.value);
  unsuppressee.value = "";
}
</script>
<template>
  <h2>Suppress/unsuppress users</h2>
  <form @submit.prevent="addSuppression" class="pure-form">
    <fieldset>
      <legend>Suppress a user</legend>
      <input type="text" placeholder="Username" v-model="suppressee" required />
      <button type="submit" class="pure-button pure-button-primary">Suppress user</button>
    </fieldset>
  </form>
  <form @submit.prevent="removeSuppression" class="pure-form">
    <fieldset>
      <legend>Unsuppress a user</legend>
      <input type="text" placeholder="Username" v-model="unsuppressee" required />
      <button type="submit" class="pure-button pure-button-primary">Unsuppress user</button>
    </fieldset>
  </form>
</template>
