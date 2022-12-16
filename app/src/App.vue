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
  console.log(values)

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
    style="display: flex; flex-direction: column; align-items: start; justify-content: space-around"
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
    <span>{{ errors.email }}</span>
    <label for="password">Mot de passe :</label>
    <Field :as="'input'" name="password" type="password"/>
    <span>{{ errors.password }}</span>
    <label for="adult">Êtes-vous un adulte ?</label>
    <Field :as="'input'" type="checkbox" name="adult"/>
    <span>{{ errors.adult }}</span>
    <label for="gender">Genre : </label>
    <Field :as="'select'" name="gender">
      <option value="Homme">Homme</option>
      <option value="Femme">Femme</option>
      <option value="Autre">Autre...</option>
    </Field>
    <span>{{ errors.gender }}</span>
    <button @click="handleSubmit" :disabled="isSubmitting">Envoyer</button>
  </Formik>
</template>