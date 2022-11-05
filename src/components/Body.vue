<template>
  <body>



<div id="container_wrapper">
  


<div id="main_card_container">
    <div class="card_container" v-for="output_cards in sendCards">

        <h2 class="counter_css">  {{ output_cards.amount }} </h2>
        <img v-bind:id="output_cards.id"  class="img_size" v-on:click="minusCard($event)" v-bind:src="output_cards.img">


        <div class="procent_bar">
            <div v-bind:style="{width: output_cards.chance + '%' }"> </div>
            <h2 class="chance_number">{{ output_cards.chance }} % </h2>
        </div>
        
    </div>
</div>



  <hi-low-app></hi-low-app>



</div>


  </body>
</template>








<script>
import { bus } from '../main';
import Hi_low from './Hilow.vue';



export default {
  components:{
      'hi-low-app':Hi_low

  },
  props:{
    sendCards:{
      type:Array,
      required:true
    }
  },
  data () {
    return {
     
 
    }
  },
  methods:{
    minusCard:function(event){



        //find the higste number-----------------------------------------------------------
        var highestNumbers = [];

        //find the higste number-----------------------------------------------------------




        // get the id from html id="2"
        // event.currentTarget.id 
        //console.log(event.currentTarget.id);

        // insert the id into -- this.cards[   event.currentTarget.id   ].amount
        // so we can find the right array that we click on to subtract
        // console.log(    this.sendCards[    event.currentTarget.id     ].amount   );

        //prevent it from going pass zero 
         if (this.sendCards[event.currentTarget.id].amount <=0){
            this.sendCards[event.currentTarget.id].amount = 0;
         }else{

            this.sendCards[event.currentTarget.id].amount--;

            for (var i = 0; i < this.sendCards.length; i++) {
                  
                this.sendCards[i].deck--;              
                this.sendCards[i].chance = ((this.sendCards[i].amount/this.sendCards[i].deck)*100).toFixed(2);




                
        //find the higste number-----------------------------------------------------------
                //push in the array
                highestNumbers.push( parseFloat(this.sendCards[i].chance) );

        //find the higste number-----------------------------------------------------------




            }
            // this.sendCards[0].addChance =  this.sendCards[0].chance;
            // this.sendCards[1].addChance =  this.sendCards[0].chance +  this.sendCards[1].chance;
         }



        //find the higste number-----------------------------------------------------------
        //Sorting an Array
        highestNumbers.sort(); 
        highestNumbers.sort(function(a,b){return b-a});
        var threeHighest = highestNumbers.slice(0,3);
        console.log(threeHighest);



        //find the higste number-----------------------------------------------------------





         // hi-low function
         //
         if (event.currentTarget.id <5) {

            bus.$emit('calHiLow', 1);
         }else if(event.currentTarget.id > 7){
            bus.$emit('calHiLow', -1);
         }else{
            bus.$emit('calHiLow', 0);
         }
     
       
    }

  }
}
</script>













<style scoped>


.card_container{
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-evenly;
}
h2.counter_css {
    width: 30px;
    margin-right: 10px;
}

.img_size:hover{
  cursor: pointer;
}
.procent_bar{
  height: 30px;
  width: 400px;

  border:2px solid #000;
}

.procent_bar div{
  height: 30px;
  background-color: #26c281;


}





.chance_number {
    text-align: center;
    z-index: 200;
    position: relative;
    width: 400px;
    top: -28px;
    color: #e74c3c;
}





div#container_wrapper {
    display: flex;
    justify-content: space-evenly;
  
}



div#hi_low {
    display: flex;
    flex-direction: column;
    justify-content: center;
}



#main_card_container{
  
}


#hi_low_wrapper{

    flex: 1 1 auto;
    display: flex;
    flex-direction: column;

}


</style>
