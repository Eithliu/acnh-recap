<template>
  <div class="hello">
    <p> {{  }}Les villageois </p>
    <div class="grille">
      <ul v-for="villager in villagers" :key="villager.id" class="cards">
        <img :src="villager.icon_uri" class="img-card"/>
        <li>Personality: {{ villager.personality }}</li>
        <li>Saying: <em>{{ villager.saying }}</em></li>
      </ul>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'HelloWorld',
  props: {
    msg: String,
  },
  data() {
    return {
      img_url: null,
      villagers: null,
    }
  },
  mounted() {
    axios.get('https://acnhapi.com/v1/villagers').then((response) => this.villagers = response.data)
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.cards {
  box-shadow: 2px 2px 5px #afafaf;
  border-radius: 10px;
  padding-bottom: 20px;
}
ul.cards{
  display: flex;
  flex-direction: column;
}
div.grille {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 10px;
  grid-auto-rows: minmax(100px, auto);
}
ul > img.img-card {
  width: 30%;
  align-self: center;
}
</style>
