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
import { defineProps, defineEmits, inject } from "vue";

const formikData = inject('formik-data')

defineEmits(['update:modelValue'])

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