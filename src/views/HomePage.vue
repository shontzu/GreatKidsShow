<template>
  <div>
    <img v-if="bg === 1" src="../assets/bg-home-beach.png" alt="background image" class="bg-img" data-aos="fade-down" data-aos-duration="1500" />
    <img v-else-if="bg === 2" src="../assets/bg-home-skyline.png" alt="background image" class="bg-img" data-aos="fade-down" data-aos-duration="1500" />
    <img  v-else-if="bg === 3" src="../assets/bg-home-garden.png" alt="background image" class="bg-img" data-aos="fade-down" data-aos-duration="1500" />
    <img  v-else src="../assets/bg-home-mount.png" alt="background image" class="bg-img" data-aos="fade-down" data-aos-duration="1500" />
    <!-- on button click (line 10-13) the bg data (which is default at 0 on line 60) will be be changed.
     if-else statement (line 3-6) determine which img gets rendered as background depending on button click -->
    <div class="change-bg" >
      <md-button @click="bg=0">Mountain</md-button>
      <md-button @click="bg=1">Beach</md-button>
      <md-button @click="bg=2">Skyline</md-button>
      <md-button @click="bg=3">Garden</md-button>
    </div>
    <h1 data-aos="fade-up" data-aos-duration="900">HOME</h1>

    <!-- Introduction video -->
    <video controls data-aos="slide-right" data-aos-duration="1500" poster="../assets/thumbnail-team.png" >
      <source src="../assets/vid-group.mp4" type="video/mp4" />
      Your browser does not support the video tag.
    </video>
    <!-- end introduction video  -->

    <!-- horizontal scrolling gallery -->
    <h2 data-aos="fade-up" data-aos-duration="1500"><i>☆☆☆ FEATURED ☆☆☆</i></h2>
    <VideoGallery
      :cartoons="featuredCartoon"
      data-aos="slide-left"
      data-aos-duration="1500"
    />
    <!-- end horiozontal scrolling gallery -->

    <!-- another horizontal scrolling gallery -->
    <h2 data-aos="fade-up" data-aos-duration="1700"><i>☆☆☆ TRENDING ☆☆☆</i></h2>
    <VideoGallery
      :cartoons="trendingCartoon"
      data-aos="slide-left"
      data-aos-duration="1500"
    />
    <!-- end horizontal scrolling gallery -->
    <br /><br /><br />
    <Footer />
    <Modal />
  </div>
</template>

<script>
import { ref } from "@vue/composition-api";
import VideoGallery from "../components/VideoGallery.vue";
import Modal from "../components/ModalWelcome.vue"
import Footer from "../components/Footer.vue"
import featuredCartoonData from "@/data/featuredCartoon.json";
import trendingCartoonData from "@/data/trendingCartoon.json";
// if your crush knows binary
// they'd think you're a 10
// Shon Tzu.K (2021)

export default {
  name: "HomePage",
  data: function() {
    return {
      bg: 0
    }
  },
  components: {
    VideoGallery,
    Modal,
    Footer,
  },

  setup() {
    const featuredCartoon = ref(featuredCartoonData);
    const trendingCartoon = ref(trendingCartoonData);
    return { featuredCartoon, trendingCartoon };
  },
};
</script>

<style scoped>
.bg-img {
  border-radius: 0%;
  position: fixed;
  left: 0;
  z-index: -1;
  object-fit: cover;
  height: 100vh;
  width: 100vw;
}
.change-bg {
  padding-top:5vh; 
  display:flex; 
  justify-content:space-evenly;
  align-items:center; 
}
@media screen and (max-width: 1000px) {
  .change-bg {
    display:block;
  }
}
</style>
