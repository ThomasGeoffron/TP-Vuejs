<template>
    <component
        :is="props.as"
        :name="name"
        :value="formikData.values[name]"
        @input="( event ) => formikData.updateValue(name, event.target.value)"
    >
        <slot/>
    </component>
</template>

<script setup>
import { defineProps, defineEmits, inject } from "vue";

const formikData = inject('formik-data')

const props = defineProps({
    as: {
        type: String || Object,
        required: true,
        default: 'input'
    },
    name: {
        type: String,
        required: true,
    }
});

</script>