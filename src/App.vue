<template>
  <div id="nav">
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </div>
  <router-view/>
</template>

<script lang="ts">
import { defineComponent, onMounted } from 'vue'
import axios from 'axios'
import jsonp from 'jsonp'

export default defineComponent({
  setup() {
    onMounted(()=> {
      // let url = 'https://www.easy-mock.com/mock/5b012c1fe6e1035843cd3aff/mockapi/table/list'
      let url = '/api/activity/servicetime'
      axios.get(url).then((resp) => {
        console.log(resp.data)
        console.log('axios')
      })

      let url2 ='https://www.imooc.com/activity/servicetime'
      jsonp(url2,(err,res) => {
        console.log(res)
      })


    })
    
  },

})
</script>


<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
