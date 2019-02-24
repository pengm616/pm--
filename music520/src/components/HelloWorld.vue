<template>
  <div id="helloWorld">
    <h1>{{msg}}</h1>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  components:{},
  data () {
    return {
      msg: '你好，world'
    }
  }
}
</script>

<style scoped>

</style>