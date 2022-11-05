

<template>
  <div id="hi_low">



 <h2>True Count: {{ trueCount }}</h2>
    <h2>Hi-Low: {{ hi_low }}</h2>

  
    
<h2>Number Of Decks: {{ numberOfDecks }}</h2>

  </div>
</template>






<script>
import { bus } from '../main';


	export default {
	  data () {
	    return {
	        hi_low:0,
	        numberOfDecks:0,


	        cards:52,

	        trueCount:0
	        
	       
	    }
	  },
	  created(){
	  	//this is hi low
	  	// subtract or add
	  	bus.$on('calHiLow',(data) =>{

	  		this.hi_low += data;

	  
 		    if (this.cards == 0) {
	  			this.cards = 52;

	  			this.numberOfDecks--;
	  		}else{
	  			this.cards--;
	  		}

		this.trueCount = this.hi_low / this.numberOfDecks;
	  		

	  	}),
	  	// get the number Of Decks  ---  4
	  	bus.$on('numberOfDecks',(data) =>{
	  		this.numberOfDecks = data;
	  	})


	  }
	}




</script>










<style scoped>

p{
	text-align: center;
}


</style>
