<template>
  <div class="tab-control">
    <div v-for="(item,index) in titles" :key="item"
        class="tab-control-item">
        <span :class="{active:index===currentIndex}" @click="itemClick(index)">{{item}}</span>
    </div>
  </div>
</template>

<script>
export default {
    name:'TabControl',
    props:{
        titles:{
            type:Array,
            default(){
                return[]
            }
        }
    },
    data(){
        return{
            currentIndex:0
        }
    },
    methods:{
        itemClick(index){
            this.currentIndex=index
        }
    }
}
</script>

<style>
    .tab-control{
        display: flex;
    }
    .tab-control-item{
        flex: 1;
        font-size: 15;
        height: 40px;
        line-height: 40px;
        text-align: center;
    }
    .tab-control-item span{
        padding: 5px;
    }
    .active{
        color: var(--color-high-text);
        border-bottom: 3px solid var(--color-tint);

    }
</style>