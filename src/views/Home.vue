<template>
  <div class="home">
    <Search />
    <ul>
      <li v-for="photo in photos" :key="photo.urls.regular">
        {{ photo.urls.regular }}
      </li>
    </ul>
   <Images 
   msn="Images component i Home sida"/>
  </div>
</template>

<script>
// @ is an alias to /src
import * as API from '../router/mock.js'
import Search from "@/components/Search.vue";
import Images from "@/components/Images.vue";
 

export default {
  name: "Home",
  props : {
    photourl:Object
  },
  components :{Search, Images},
  data() {
    return {
      photos: [],
    };
  },
  async created() {
    this.photos = await API.fetchImages();
    return API.results
    // const data = await request.json();
    // this.photos = data.results;
  },
};
</script>

 <style>

 </style>
