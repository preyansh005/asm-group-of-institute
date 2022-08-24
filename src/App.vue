<template>
  <Input />
</template>

<script>
import Input from './components/Input.vue'

export default {
  name: 'App',
  components:{
    Input,
  }
}
</script>

<style>
*{
  background: #18454A;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #FF5A59;
  margin-top: 60px;
}
</style>