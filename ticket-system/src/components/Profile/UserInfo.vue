<template>
  <v-sheet width="600" class="mx-auto"><form @submit.prevent="submit">
    <v-text-field
      v-model="name.value.value"
      :error-messages="name.errorMessage.value"
      label="Имя"
    ></v-text-field>

    <v-text-field
      v-model="phone.value.value"
      :error-messages="phone.errorMessage.value"
      label="Номер телефона"
    ></v-text-field>

    <v-text-field
      v-model="email.value.value"
      :error-messages="email.errorMessage.value"
      label="E-mail"
    ></v-text-field>

    <v-btn
      class="me-4"
      type="submit"
    >
      submit
    </v-btn>

    <v-btn @click="handleReset">
      clear
    </v-btn>
  </form></v-sheet>
</template>
  
<script setup>

  import { ref } from 'vue'
  import { useField, useForm } from 'vee-validate'

  const { handleSubmit, handleReset } = useForm({
    validationSchema: {
      name (value) {
        if (value?.length >= 2) return true

        return 'Имя должно содержать не менее 2 символов.'
      },
      phone (value) {
        if (value?.length > 9 && /[0-9-]+/.test(value)) return true

        return 'Номер телефона должен состоять как минимум из 9 цифр'
      },
      email (value) {
        if (/^[a-z.-|0-9]+@[a-z.-]+\.[a-z]+$/i.test(value)) return true

        return 'Должен быть действительный адрес электронной почты.'
      },
    },
  })
  const name = useField('name')
  const phone = useField('phone')
  const email = useField('email')
  const select = useField('select')
  const checkbox = useField('checkbox')

  const items = ref([
    'Item 1',
    'Item 2',
    'Item 3',
    'Item 4',
  ])

  const submit = handleSubmit(values => {
    alert(JSON.stringify(values, null, 2))
  })
</script>

  