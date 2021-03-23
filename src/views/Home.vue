<template>
  <div class="home">
    <el-button @click="test">测试</el-button>
  </div>
</template>

<script>

export default {
  name: 'Home',
  components: {
  },
  methods:{
    test(){
      this.$request.get('/user/test').then(e=>{
        console.log(e);
      })
    }
  }
}
</script>
