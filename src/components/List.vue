<template lang="pug">
  div(class="main-div")
    ul(class="ul-without-symbol")
      ItemOfList(
        v-for="hotdog in GET_HOTDOGS"
        :hotdog="hotdog"
        :key="hotdog.index"
      )
</template>

<script>
  import ItemOfList from "./ItemOfList";
  import axios from 'axios'
  import {mapGetters} from "vuex";
    export default {
      components:{
        ItemOfList
      },
      name: "List",
      data(){
          return{
          }
      },
      computed:{
        ...mapGetters(['GET_HOTDOGS'])
      },
      mounted() {
        axios
          .get('https://eliftechschool.herokuapp.com/hotdog',{
          })
          .then(response => (this.$store.commit('SET_HOTDOGS',response.data.hotdog)))
      },
    }
</script>

<style scoped>
  .main-div{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .ul-without-symbol{
    list-style: none;
    margin-bottom: 15px;

  }
</style>
