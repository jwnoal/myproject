<template>
  <div id='NoalBody' class="NoalBody">{{me}}</div>
</template>

<script>
window.onload=function(){
	var bodyheight=document.body.offsetHeight-80+'px';
	var NoalBody=document.getElementById('NoalBody');
	NoalBody.style.height=bodyheight;
}

export default {
  name: 'NoalBody',
  data () {
    return {
     me:'df'
    }
  },
  methods:{
  	
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
	.NoalBody{width: 100%;background: url(../assets/container-bg.jpg) no-repeat;background-size: 100% 100%;}
</style>
