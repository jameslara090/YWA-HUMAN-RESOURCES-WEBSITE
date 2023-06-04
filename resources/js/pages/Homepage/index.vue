
  <template>
      <v-carousel
      v-model="currentSlide"
      :interval="slideInterval"
      height="520"
      show-arrows="hover"
      show-dots
      hide-delimiter-background
      cycle
    >

    <v-carousel-item v-for="(item, index) in items" :key="index">      
            <v-sheet
              v-if="showTimer"
              :value="timerProgress"
              height="5"
              background-color="grey lighten-2"
              :class="img-opacity"
              :height="600"
            >
          <v-img :src="item.src" class="img-opacity" height="600" :alt="item.alt"></v-img>
            <div class="text-overlay">
                  <div class="text-h3">
                  Work Abroad Now with Your YWA Partner and We Deploy a {{ item.alt }}
                  </div>
                  <br>
                  <v-btn :color="indigo">
                      Apply Now
                   </v-btn>

            </div>
            </v-sheet>
     </v-carousel-item>
    </v-carousel>
    
  </template>

  <style scoped>
      .text-overlay {
        position: absolute;
        top: 50%; /* Positions the text 50% from the top */
        left: 50%; /* Positions the text 50% from the left */
        transform: translate(-50%, -50%); /* Centers the text using negative translate */
        text-align: center; /* Centers the text horizontally */
        color: #fff; /* Optional text color for the overlay */
        padding: 10px; /* Optional padding for the overlay */
      }
    .img-opacity{
      position: relative;
     }
     .img-opacity:after{
      content: "";
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(30, 4, 92, 0.5); /* Change the color and opacity values as per your requirement */
     }
  </style>
  

<script>
export default {
  data() {
    return {
      currentSlide: 0,
      slideInterval: 6000, // Interval between slides in milliseconds
      showTimer: true,
      timerProgress: 0,
      items: [
        { src: "../images/welder.jpg", alt: "Welder" },
        { src: "../images/electrician1.jpg", alt: "Electrician" },
        { src: "../images/carpenter.jpg", alt: "Carpenter" },
        { src: "../images/health-care.jpg", alt: "Health Care Assistance" },
      ],
    };
  },
  mounted() {
    if (this.showTimer) {
      this.startTimer();
    }
  },
  methods: {
    nextSlide() {
      this.currentSlide = (this.currentSlide + 1) % this.items.length;
      if (this.showTimer) {
        this.timerProgress = 0;
        this.startTimer();
      }
    },
    startTimer() {
      let progress = 0;
      const interval = setInterval(() => {
        progress += (100 / this.slideInterval) * 100;
        this.timerProgress = Math.min(progress, 100);
        if (progress >= 100) {
          clearInterval(interval);
          this.nextSlide();
        }
      }, 100);
    },
  },
};
</script>

<style>

</style>