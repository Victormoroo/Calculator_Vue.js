<template>
  <div>
    <h1>Hello Vue!</h1>
    <p>My name is {{nome}}</p>
    <p>I'm a {{profissao}}</p>
  </div>
</template>

<script>
  export default {
    name: 'Calculator',

    data() {
      return {
        nome: 'Victor',
        profissao: 'programming student'
      }
    },

    methods: {

    }
  }
</script>
