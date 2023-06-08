<template>
  <v-row>
      <v-col cols="12">
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
                      YWA is now inviting you to Apply Abroad. We'll Help you to achieved your Dreams
                        of becoming Professional
                      </div>
                      <br>
                      <v-btn :color="indigo" :class="text-h2">
                          Apply Now
                      </v-btn>

                </div>
                </v-sheet>
        </v-carousel-item>
      </v-carousel>
      </v-col>

      <v-col cols="12">
        <v-card
                class="mx-auto"
                max-width="1000"
                variant="outlined"
                color="#311B9"
                :class="pt-9">
            <v-form v-model="valid">
            <v-container class="pl-14 pt-5 pb-4">
              <v-row>
                <v-col
                  cols="12"
                  md="3"
                >
                  <v-text-field
                    label="Enter Keywords"
                  ></v-text-field>
                </v-col>

                <v-col
                  cols="12"
                  md="3"
                >
                <v-select
                  label="Job Classification"   
                   ></v-select>
                </v-col>

                <v-col cols="12" md="3">
                  <v-select
                  label="Location"   
                   ></v-select>
                </v-col>
                <v-col cols="12" md="3">
                <v-card-actions>
                  <v-btn color="primary" variant="outlined">
                    <v-icon left>mdi-magnify</v-icon>Search
                  </v-btn>
                </v-card-actions>
                </v-col>
              </v-row>
            </v-container>
          </v-form>
          </v-card>
      </v-col>

     <v-container>
       <v-row>
        <v-divider :thickness="10" color="info" vertical></v-divider>
            <v-col cols="4" :justify="center">
                <h1 style="padding-top: 9.5rem;">Availables Jobs</h1>
            </v-col>
            <v-col cols="8">
              <v-carousel
            v-model="currentSlide"
            :interval="slideInterval"
            height="350"
            show-arrows="hover"
            show-dots   
            hide-delimiter-background
            cycle
            >
          
            <v-col cols="12">
        
            </v-col>
            </v-carousel>
            </v-col>
       </v-row> 
     </v-container> 
  </v-row>
  
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
      slides: [
        ['Item 1', 'Item 2', 'Item 3', 'Item 4'],
        ['Item 5', 'Item 6', 'Item 7', 'Item 8'],
        ['Item 9', 'Item 10', 'Item 11', 'Item 12']
        // Add more rows or modify as needed
      ]
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