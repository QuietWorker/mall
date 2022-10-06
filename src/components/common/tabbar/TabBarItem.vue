<template>
  <div class="tab-bar-item" @click="itemClick">
    <div v-if="!isActive"><slot name="item-icon"></slot></div>
    <div v-else><slot name="item-icon-active"></slot></div>
    <div :style="activeStyle" :class="{active:isActive}"><slot name="item-text"></slot></div>
  </div>
</template>

<script>

export default {
    name:"TabBarItem",
    data(){
      return{
        
      }
    },
    computed:{
      isActive(){
        return this.$route.path.indexOf(this.path)!==-1    //如果不等于-1  说明找到了这个路径 即选中
        /* indexOf() 方法可返回某个指定的字符串值在字符串中首次出现的位置。
          如果没有找到匹配的字符串则返回 -1。 */
          /* var str="Hello world, welcome to the universe.";
        var n=str.indexOf("welcome"); // 输出结果是13   如果找不到welcome 则返回 -1 */
      },
      activeStyle(){
        return this.isActive?{color:this.activeColor}:{}
      }
    },
    props:{
      path:String,
      activeColor:{
          type:String,
          default:'red'
        }
    },
    methods:{
      itemClick(){
        this.$router.push(this.path)
      }
    }
    
}
</script>

<style>
    .tab-bar-item{
    flex: 1;
    text-align: center;
    height: 49px;
    font-size: 14px;
    } 
    .tab-bar-item img{
        width: 24px;
        height: 24px;
        margin-top: 3px;
        vertical-align: middle;
        margin-bottom: 2px;
    }
    .active{
      color: red;
    }
</style>