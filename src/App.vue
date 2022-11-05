<template>
  <div id="main_blackjack_wrapper">


    <header-app v-on:changeNumberOfDeck="updateDeck($event)"></header-app>
  
    <body-app v-bind:sendCards="cards"></body-app>

  

    <footer-app ></footer-app>


  </div>
</template>

<script>

import Body from './components/Body.vue';
import Header from './components/Header.vue';
import Footer from './components/Footer.vue';





export default {
  components:{
      'header-app':Header,
      'body-app':Body,
      'footer-app':Footer
  },
  data () {
    return {
     
      cards:[
        {id: 0, img:'cards_img/2D.png', amount: 4, name: '2D', deck:52, chance: 0, addChance: 0},
        {id: 1, img:'cards_img/3D.png', amount: 4, name: '3D', deck:52, chance: 0, addChance: 0},
        {id: 2, img:'cards_img/4D.png', amount: 4, name: '4D', deck:52, chance: 0, addChance: 0},
        {id: 3, img:'cards_img/5D.png', amount: 4, name: '5D', deck:52, chance: 0, addChance: 0},
        {id: 4, img:'cards_img/6D.png', amount: 4, name: '6D', deck:52, chance: 0, addChance: 0},
        {id: 5, img:'cards_img/7D.png', amount: 4, name: '7D', deck:52, chance: 0, addChance: 0},
        {id: 6, img:'cards_img/8D.png', amount: 4, name: '8D', deck:52, chance: 0, addChance: 0},
        {id: 7, img:'cards_img/9D.png', amount: 4, name: '9D', deck:52, chance: 0, addChance: 0},
        {id: 8, img:'cards_img/10D.png', amount: 16, name: '10D', deck:52, chance: 0, addChance: 0},
        {id: 9, img:'cards_img/AD.png', amount: 4, name: 'AD', deck:52, chance: 0, addChance: 0}
     
      ]
      
    }
  },
  methods:{
    updateDeck:function(update){


   



        //update is from Header.vue with --- this.$emit('changeNumberOfDeck', this.$refs.my_input.value); value is from the input field
        //console.log(update);
        this.deck = this.deck * update;
        //loop through the cards and change the amount  
        //console.log(this.cards[0].amount);
        for (var i = 0; i < this.cards.length; i++) {
          
            this.cards[i].amount = this.cards[i].amount*update;
            this.cards[i].deck = this.cards[i].deck*update;

            this.cards[i].chance = ((this.cards[i].amount/this.cards[i].deck)*100).toFixed(2);
                            
        }




    }
  }
}
</script>













<style>

.img_size{
  width:38px;
  height: 100%;
   transform: rotate(90deg);
}

*{
  margin: 0px;
  padding: 0px;
}
html {
  background-color: #266D5D;
  height: 100%;
}


</style>
