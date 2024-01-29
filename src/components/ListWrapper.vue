<template>
  <div>
    <input type="text" placeholder="Search..." v-model="text">
  </div>

  <div style="color: white; margin: 20px; font-weight: bold;" v-if="veri==true && loading==false">There data not found</div>
  <div class="list" v-else-if="veri==false && loading==false">
    <ul>
        <li v-for="item in data" :key="item">
          <list-render :data="item" />
        </li>
    </ul>
  </div>
  <Loading v-if="loading"></Loading>



</template>

<script>
import axios from 'axios';
import Loading from './Loading.vue';
import ListRender from './ListRender.vue';
export default {
    name:'ListWrapper',
    components: { Loading,ListRender },
    data(){
        return{
            text:'',
            veri:true,
            data:[],
            loading:false,
        }
    },
    methods:{
        async fetchdata(text){
            this.loading = true;
             await axios.get(`https://images-api.nasa.gov/search?q=${text}`)
            .then(res=>{ this.data=res.data.collection.items });
         this.loading = false;
        }
    },
    watch:{
        text(newv){
            if(newv.length>2){
                this.fetchdata(newv);
                this.veri=false;
            }
            else{
                this.veri = true;
            }
        }
    }

}
</script>

<style>
    input{
        width: 100%;
        padding: 10px;
        font-size: 17px;
        border: 1px solid #ccc;
        border-radius: 0px 0px 10px 10px;
    }
    ul{
        margin-top: 60px;
        columns: 4;
        column-gap: 2em;
    }
    .list{
        display: flex;
        flex-wrap: wrap;
        justify-content: space-around;
    }
    li{
        margin-top: 20px;
    }
</style>