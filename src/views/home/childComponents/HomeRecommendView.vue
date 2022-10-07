<template>
  <div class="recommend">
    <div v-for="item in recommends" class="recommend-item" :key="item.sort">
        <a :href="item.link">
            <img :src="item.image" alt="">
            <div>{{item.title}}</div>
        </a>
    </div>
  </div>
</template>

<script>
export default {
    name:"HomeRecommendView",
    props:{
        recommends:{
            type:Array,
            default(){
                return[]
            }
        }
    }
}
</script>

<style>
    .recommend{
        display: flex;
        width: 100%;
        text-align: center;
        padding: 10px 0 20px;
        font-size: 12px;
        border-bottom: 8px solid #eee;
    }
    .recommend-item{
        flex: 1;
    }
    .recommend-item img{
        width: 80px;
        height: 80px;
    }
</style>