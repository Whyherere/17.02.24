<template>
    <v-sheet width="300" class="mx-auto">
      <v-form @submit.prevent>
        <v-text-field
          v-model="login"
          :rules="rulesLogin"
          label="Логин"
        />
        <v-text-field
          v-model="password"
          :rules="rulesPass"
          label="Пароль"
          type="password"
        />
        <v-btn @click="checkData" type="submit" block class="mt-2">Submit</v-btn>
      </v-form>
    </v-sheet>
  </template>
  
  <script>
  
  export default {
    name: 'LoginForm',
  
    components: {
    },
  
    data: () => ({
      login: '',
      password: '',
      rulesLogin: [
        value => {
          if (value) {
            return true
          }

          if (value.length < 5) {
            return 'Ваш логин должен быть больше 5 символов'
          }

          return 'Поле не должно быть пустым'
        },
      ],
      rulesPass: [
        value => {
          if (value) {
            return true
          }

          if (value.length < 5) {
            return 'Ваш пароль должен быть больше 5 символов'
          }

          return 'Поле не должно быть пустым'
        },
      ],
    }),
    methods: {
        checkData() {
            if (this.login == '' || this.password == '') {
                return
            }

            this.$router.push('/')
        }
    }
  }
  </script>
  