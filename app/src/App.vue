<script setup>
import HelloWorld from './components/HelloWorld.vue'
import Formik from "./components/Formik.vue"
import Field from "./components/Field.vue"

const initialValues = {
  email: "johndoe@example.com",
  password: "",
  adult: false,
  gender: "",
};

const validate = (values) => {
  const errors = {}

  if (!values.email) {
    errors.email = "Aucun email renseigné";
  }

  if (!values.password) {
    errors.password = "Aucun mot de passe renseigné";
  }

  if (!values.adult) {
    errors.adult = "Vous n'êtes pas un adulte !";
  }

  if (!values.genre) {
    errors.gender = "Aucun genre renseigné";
  }

  return errors;
};

</script>

<template>
  <Formik 
    v-slot="{
      values,
      errors,
      handleSubmit,
      isSubmitting,
    }"
    :initialValues="initialValues"
    :validate="validate"
  >
    <label for="email">Email :</label>
    <Field :as="'input'" name="email"/>
    <label for="password">Mot de passe :</label>
    <Field :as="'input'" name="password" type="password"/>
    <label for="adult">Êtes-vous un adulte ?</label>
    <Field :as="'input'" type="checkbox" name="adult"/>
    <label for="gender">Genre : </label>
    <Field :as="'select'" name="gender">
      <option value="Homme">Homme</option>
      <option value="Femme">Femme</option>
      <option value="Autre">Autre...</option>
    </Field>
    <button @click="handleSubmit" :disabled="isSubmitting">Envoyer</button>
    <p v-if="errors">Il y a des erreurs</p>
  </Formik>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
