<template>
  <div class="wellcome" ref="wellcome">
    Welcome Transition Main Page {{ reamingpage }} sn.
  </div>
</template>

<script>
import axios from "axios";
export default {
    name:'Wellcome',
    data() {
        return {
          reamingpage:5,
        }
    },
    created() {
        const a = async ()=>{
            let b= await axios.get('https://api.nasa.gov/planetary/apod?api_key=hYS0wioZOEJ8e5PRRedeJN37lPDCbu9wE5LTNYNR');
            this.background=b.data.hdurl;
            console.log(this.background);
            this.$refs.wellcome.style.background=`url(${this.background}) no-repeat fixed center`;
            return b;
        } ;
        a();
        setInterval(()=>{
            this.reamingpage--;
        },1000);
    },


}
</script>

<style>
  .wellcome{
        width: 100vw;
        height: 100vh;
        background-size: cover;
        background-position: center;
        background-repeat: no-repeat;
        display: flex;
        justify-content: center;
        align-items: center;
        color: white;
        font-size: 30px;
    }
</style>