<template>
  <div id="app">
    <h2 class="title">{{ title }}</h2>

    <div style="max-width:100%">
      <center>
        <input type="search" class="search-bar" v-on:input="filter = $event.target.value" name="search" placeholder="Filtre por aqui">
      </center>
      <gallery v-bind:pictures='filteredPictures' ></gallery>
      
    </div>

  </div>
</template>

<script>

  import gallery from './components/shared/gallery/gallery.vue';


  export default {
    data(){
      return {
        title: 'PlanetPic',
        pictures: [],
        filter: ''
      }
    },
    components:{'gallery':gallery},
    created(){
      let picturesPromise = this.$http.get('http://localhost:3000/v1/fotos');
      picturesPromise.then(response => this.pictures = response.data);
      
    },
    methods:{
      getFilter(value){
        this.filter = value;
      }
    },
    computed:{
      filteredPictures(){
        if(this.filter){
          let exp = new RegExp(this.filter.trim(),'i');
          return this.pictures.filter(pic => exp.test(pic.titulo));
        }else{
          return this.pictures;
        }
      }
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
 .search-bar{
        padding: 10px 12px;
        display: block;
        width: 90%;
        border-radius: 6px;
        border: none;
        font-weight: 600;
    }

    .search-bar:focus{
        outline: none;
    }
</style>
