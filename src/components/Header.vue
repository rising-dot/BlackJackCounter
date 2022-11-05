<template>



  <header>

    <h1>How many deck:</h1>

    <input type="number" ref="my_input">
    <button v-on:click="insertDeck">Submit</button>

  </header>
</template>










<script>
import { bus } from '../main';

  export default {

    data () {
      return {
        showCounter: 0,
        title:'hiiiii'
      }
    },
    methods:{
      insertDeck:function(){
        // this.showCounter = this.$refs.my_input.value;
         //this.cards.amount = 10;
         this.$emit('changeNumberOfDeck', this.$refs.my_input.value);

         bus.$emit('numberOfDecks', this.$refs.my_input.value);
      }
    }
  }



</script>











<style scoped>
  header{
    display: flex;
    align-items: center;
  }

  input[type="number"] {
      width: 53px;
  }

</style>
