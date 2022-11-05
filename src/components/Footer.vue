<template>
  <footer id="footer">



  	 <a v-bind:href = "hreflink" target = "_blank"><p>How to count cards with high low method.</p></a>

  </footer>
</template>

<script>








  
export default {


  data () {
    return {
       hreflink : "https://www.blackjackapprenticeship.com/how-to-count-cards/"
    }
  }
}
</script>










<style scoped>

p{
	text-align: center;
}
footer#footer {
    padding: 10px;
}

</style>
