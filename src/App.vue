<template>
  <div id="app">
    <h2 class="title">{{ title }}</h2>

    <div style="max-width:100%">
      <gallery v-bind:pictures='pictures' > </gallery>
    </div>

  </div>
</template>

<script>

  import gallery from './components/shared/gallery/gallery.vue';

  export default {
    data(){
      return {
        title: 'PlanetPic',
        pictures: []
      }
    },
    components:{'gallery':gallery},
    created(){
      let picturesPromise = this.$http.get('http://localhost:3000/v1/fotos');
      picturesPromise.then(response => this.pictures = response.data);
      
    }
  }
</script>


<style>

.title{
  width:100;
  text-align: center;
}

html,
body,
#app {
  padding:0;
  margin:0;
  border: 0;
  background: #190e27;
  font-family: Rubik, Roboto,sans-serif;
  color: #fefefe;
  box-sizing: border-box;
}

</style>
