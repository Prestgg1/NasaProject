<script>
import ListWrapper from './components/ListWrapper.vue';
import Wellcome from './components/Wellcome.vue';

export default{
  components:{
    Wellcome,
    ListWrapper,
    
  },
  name:'App',
  data(){
    return{
      isWellecome: true,
      Component:Wellcome,
    }
  },
  mounted(){
    setTimeout(()=>{
      this.isWellecome = false;
      this.Component = ListWrapper;
    },5000)
  }
}

</script>

<template>
  <Component :is="Component"></Component>
</template>

<style scoped>


</style>
