<script setup>
import HelloWorld from './components/HelloWorld.vue'
import Formik from "./components/Formik.vue"
import Field from "./components/Field.vue"

const initialValues = {
  email: "johndoe@example.com",
  password: "",
  adult: false,
  genre: "",
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
    errors.genre = "Aucun genre renseigné";
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
    <Field :as="'input'" name="email"/>
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
