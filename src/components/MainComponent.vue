<template>
  <main>
    <div class="container ">
      <div class="songCard" v-for="(items, index) in songCards" :key="index">
        <div class="card">
          <img :src="items.poster" alt="" />
          <div class="card-text">
            <h4>{{ items.title }}</h4>
            <p>{{ items.author }}</p>
            <p>{{ items.year }}</p>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import axios from "axios";

export default {
  name: "MainComponent",
  data() {
    return {
      songCards: {},
    };
  },
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((res) => {
        this.songCards = res.data.response;
        console.log(res.data);
      })
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>

<style scoped>
main {
  background-color: hsl(209deg 33% 17%);
  height: calc(100vh - 60px);
}
.songCard {
  width: calc((100% / 5) - 20px);
height: 250px;
  text-align: center;
  background-color: hsl(210deg 21% 23%);
  margin: 10px auto;
}
.card {
  display: flex;
  flex-flow: column;
  justify-content: center;
}
img {
  height: 140px;
  padding: 15px;
}
h4{
    color: white;
    margin-bottom:10px ;
    padding: 0 5px;
}
p{
    color: hsl(217deg 4% 36%);
    font-size: 14px;
}
.container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  padding-top: 70px;
}
</style>
