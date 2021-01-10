<template>
  <div id="app">
    <a href="#" @click.prevent="login">login</a>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'App',
  methods: {
    async login() {
      await axios.get('http://localhost:8000/sanctum/csrf-cookie')

      await axios.post('http://localhost:8000/login', {
        email: 'ivan@ivan.com',
        password: 'password'
      }).then(async (response) => {
        console.log('Response', response);
        let response2 = await axios.get('http://localhost:8000/api/user')

        console.log(response2)
      });

    }
  }
}
</script>
