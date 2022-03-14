<template>
  <input v-model="usernameValue" type="text" />
  <p v-if="usernameError">{{ usernameError }}</p>

  <pre>
    {{ usernameValue }}
  </pre>
</template>

<script setup lang="ts">
import { useForm, useField } from 'vee-validate';
import { z } from 'zod';
import { toFieldValidator } from '@vee-validate/zod';

const { value: usernameValue, errorMessage: usernameError } = useField(
  'username',
  toFieldValidator(z.string().nonempty({ message: 'Le champ est obligatoire' }))
    .min(3, { message: 'Le champ est trop court' })
    .max(103, { message: 'Le champ est trop long' })
);
</script>

<style scoped lang="scss"></style>
