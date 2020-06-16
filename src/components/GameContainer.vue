<template>
 <div class="game-container">
   <enemy v-for=" (key,index) in 2" :key="index" :x="Math.round((Math.random()*380)+1)" :y="0"></enemy>
   <div class="player">
     <span class="bullet"></span>
   </div>
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
      ],
    }
  },
  created(){
    window.document.onkeydown=this.onkeydown
  },
  mounted(){
  },
  methods:{
    shoot(){
    },
    onkeydown(e){
      console.log(e)
      for(let i=0,len=this.$children.length;i<len;i++){
          let item=this.$children[i]
          if(e.key===item.str)item.killed=!item.killed,item.timer=null
          this.shoot()
      }
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
  background: #ddd;
}
.player{
  position: absolute;
  transform:translate(-50%,-60px);
  top:100%;
  left:50%;
  width:60px;
  height:70px;
  background-image:url('../assets/player.gif');
  background-size:contain;
  background-repeat: no-repeat;
}
.bullet{
  position: absolute;
  top:-30px;
  left:50%;
  transform: translateX(-50%);
  width:15px;
  height:25px;
  background-image:url('../assets/bullet.gif');
  background-size:contain;
  background-repeat: no-repeat;
  background-position:center;
}
</style>