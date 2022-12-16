<template>
    <component
        :is="props.as"
        :name="name"
        :modelValue="formikData.values[name]"
        @update:modelValue="( value ) => formikData.updateValue(name, value)"
    >
        <slot/>
    </component>
</template>

<script setup>
import { defineProps, inject } from "vue";

const formikData = inject('formik-data')

const props = defineProps({
    as: {
        type: String | Object,
        required: true,
        default: 'input'
    },
    name: {
        type: String,
        required: true,
    }
});

</script>