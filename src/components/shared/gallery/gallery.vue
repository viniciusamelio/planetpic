<template>
  <li class="gallery">
    <ul v-for="picture in pictures" :key="picture.title">
      <div class="panel">
        <img width="300" height="200" :src="picture.url" :alt="picture.titulo" />
        <h3>{{ picture.titulo }}</h3>
      </div>
    </ul>
  </li>
</template>

<script>
  export default{
    props: ['pictures']
  }
</script>

<style scoped>
ul {
  padding: 10px;
  margin: 0;
}

.gallery {
  list-style: none;
  display: flex;
  padding: 20px;
  align-items: center;
  justify-content: center;
  flex-direction: row;
  flex-wrap: wrap;
  max-width: 100%;
}

.panel {
  transition: 0.4s;
}
.panel h3 {
  z-index: 5;
  position: relative;
  bottom: 50px;
  left: 0px;
  width: 101%;
  text-align: center;
  color: #fefefe;
  background: #0d021a;
  padding: 10px 0px;
  border-radius: 0px 0px 4px 4px;
}

.gallery img {
  border-radius: 4px;
  box-shadow: 0px 0px 5px rgba(88, 30, 180, 0.103);
}

.panel:hover {
  transform: translate(0, 2%);
}
</style>
