<template>
  <div class="enemy" :style="{left:left+'px',top:top+'px'}" v-show="killed">{{str}}</div>
</template>

<script>
export default {
    data(){
        return {
            top:0,
            left:0,
            timer:null,
            str:'a',
            killed:true
        }
    },
    mounted(){
        this.updateConfig([{name:'left',fun:this.random},{name:'top',fun:this.random},{name:'str',fun:this.updateStr}])
        this.move()
    },
    methods:{
        updateStr(){
            return String.fromCharCode(Math.floor( Math.random() * 26) + "a".charCodeAt(0))
        },
        updateConfig(arr){
            let me=this
            arr.forEach(function(item){
                   item.name=='top' ?  me[item.name]=item.fun(0) : me[item.name]=item.fun()
            })
        },
        random(val){
            return val!=null ? val : Math.round((Math.random()*380)+1)
        },
        move(speed=1,target=580){
            let me=this
            this.timer=setInterval(()=>{
                this.top+=speed
                if(this.top>=target){
                    clearInterval(this.timer)
                    this.updateConfig([{name:'left',fun:this.random},{name:'top',fun:this.random},{name:'str',fun:this.updateStr}])
                    setTimeout(()=>{
                       me.move()
                   },500)
                }
            },10)
           
        }
    }
}
</script>

<style scoped>
 .enemy{
     position: absolute;
     color:#fff;
     width:19px;
     height:19px;
     background:red;
     border:1px solid yellow;
 }
</style>