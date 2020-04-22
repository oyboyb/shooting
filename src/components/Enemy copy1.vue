<template>
  <div class="enemy" :style="{left:left+'px',top:top+'px'}">{{str}}</div>
</template>

<script>
export default {
    props:{
        x:{
            type:Number,
            default:0
        },
        y:{
            type:Number,
            default:0
        }
    },
    data(){
        return {
            top:0,
            left:0,
            timer:null,
            str:'a'
        }
    },
    mounted(){
        this.move()
    },
    methods:{
        updateStr(){
            return String.fromCharCode(Math.floor( Math.random() * 26) + "a".charCodeAt(0))
        },
        updateConfig(){
            arguments[0].forEach(item=>{
                if(item.name=='top'){
                    this[item.name]=item.fun(0)
                }
            })
        },
        random(val){
            return val!=null ? val : Math.round((Math.random()*380)+1)
        },
        move(speed=1,target=380){
            let me=this
            this.timer=setInterval(()=>{
                this.top+=speed
                if(this.top>=target){
                    clearInterval(this.timer)
                        this.top=0
                        this.left=Math.round((Math.random()*380)+1)
                    //    this.updateConfig([{name:'left',fun:this.updateCoor},{name:'top',fun:this.random},{name:'str',fun:this.updateStr}])
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
     width:20px;
     height:20px;
 }
</style>