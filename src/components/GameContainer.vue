<template>
 <div class="game-container">
   <enemy v-for=" (key,index) in 3" :key="index" :x="Math.round((Math.random()*380)+1)" :y="0"></enemy>
 </div>
</template>
<script>
import Enemy from './Enemy.vue'
export default {
  components:{
    Enemy
  },
  name: 'HelloWorld',
  props: {
  },
  data(){
    return{
      enemys:[
        {}
      ]
    }
  },
  created(){
    window.document.onkeydown=this.onkeydown
    
  },
  methods:{
    onkeydown(e){
      console.log(e)
    }
  }
}
</script>

<style scoped>
.game-container{
  position:relative;
  width:400px;
  height:600px;
  margin:10px auto;
  background: green;
}
</style>
