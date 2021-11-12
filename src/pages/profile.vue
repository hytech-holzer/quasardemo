<template>
  <q-page padding>
    <div class="column justify-center items-center">
    <h3>{{character.name}}</h3>
    <q-card class="my-card">
      <img :src="character.img" >
      <q-card-section>
        <div class="text-h6">{{character.name}}</div>
        <div class="text-subtitle2">{{character.nickname}}</div>
      </q-card-section>
    </q-card>
        <q-btn round color="black" icon="my_location" @click="myButtonClicked()" />

    </div>
  </q-page>
</template>

<style scoped>
  .my-card {
    width: 25%;
  }
</style>

<script>
import axios from 'axios';
export default {
  // name: 'PageName',
  async created() {
    console.log('created.');
    console.log(this.$route.params.id);
    var url = 'https://www.breakingbadapi.com/api/characters/' + this.$route.params.id;
    if (this.$route.params.id === 'random') {
      url = 'https://www.breakingbadapi.com/api/character/random';
    }
    const result = await this.$axios.get(url)
    console.log(result);
    this.character = result.data[0];
  }, 
  methods: {
    myButtonClicked() {
      console.log('button clicked.');
    } 
  },
  data () {
    return {
      character: ''
    }
  }
}
</script>
