<template>
  <div class="card">
    <img :src='data.links[0].href' alt="">
    <div class="datas">
        <h4>{{ data.data[0].title }}</h4>
    <p>{{ data.data[0].description }}</p> 
    </div>

  </div>
</template>

<script>
export default {
    name:'ListRender',
    data(){
        return{
        
        }
    },
    props:['data'],
    mounted(){
        console.log(this.data)
    }
}
</script>

<style>
    .card{
        width: 18rem;
        height: 18rem;
        border: 5px solid darkred;
        border-radius: 20px;
        text-align: center;
        box-sizing: border-box;
        overflow: hidden;
    }
    img{
        width: 100%;
        height: 50%;
        object-position: center center;
        object-fit: fill;
    }
    p{
        display: -webkit-box;
        -webkit-line-clamp: 1;
        -webkit-box-orient: vertical;
        text-wrap: nowrap;
    }
    .datas{
        display: flex;
        flex-direction: column;
        height: 50%;
        justify-content: space-around;
        align-items: center;
    }
</style>