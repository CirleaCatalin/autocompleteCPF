<template>
  <input-cpf></input-cpf>
</template>

<script>
import inputCpf from './components/inputCpf.vue'
export default {
  name: 'app',
  components: {
    "input-cpf": inputCpf
  },
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<style>

</style>
