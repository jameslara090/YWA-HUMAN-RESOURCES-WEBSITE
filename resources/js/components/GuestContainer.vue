<template>
    <v-app class="v-theme--light">
        <v-app-bar
            app
            flat
            style="background-color: rgb(231, 240, 246); top: 0px; z-index: 1080; transform: translateY(0%); position: fixed; height: 65px; left: 0px; width: calc((100% - 0px) - 0px);"
            
        >
            <v-toolbar-title>
               
                 <v-img :max-width="185" :max-height="190" src="images/Ywa.png"  lazy-src="images/Ywa.png">
                    <template v-slot:placeholder>
                                    <v-row
                                        class="fill-height ma-0"
                                        align="center"
                                        justify="center"
                                    >
                                        <v-progress-circular
                                            indeterminate
                                            color="#F72e2E"
                                        />
                                    </v-row>
                        </template>
                </v-img>
            </v-toolbar-title>
            <v-spacer></v-spacer>
            
            <!--Homepage-->
            <v-hover v-slot="{ hover}"><v-btn v-if="!isMobileView"
                plain
                @click.prevent="HomePage"
                :style="{ 'border-bottom': hover ? '5px solid #3465fc' : 'black'}"
                density="compact"
            >  
               <div class="text-col-black">Home</div> 
            </v-btn></v-hover>
            
            <!--Clients-->
            <v-hover v-slot="{ hover}"><v-btn
                plain
                @click.prevent="ClientPage"
                class="d-none d-sm-flex"
                :style="{ 'border-bottom': hover ? '5px solid #3465fc' : 'black'}"
                density="compact"
            >  
               <div class="text-col-black">Clients</div> 
            </v-btn></v-hover>
            <!--Jobs-->
            <v-hover v-slot="{ hover}"><v-btn
                plain
                @click.prevent="JobPage"
                class="d-none d-sm-flex"
                :style="{ 'border-bottom': hover ? '5px solid #3465fc' : 'black'}"
                density="compact"
            >  
               <div class="text-col-black">Jobs</div> 
            </v-btn></v-hover>
            <!--Our Industries-->
            <v-hover v-slot="{ hover}"><v-btn
                plain
                @click.prevent="OurIndustries"
                class="d-none d-sm-flex"
                :style="{ 'border-bottom': hover ? '5px solid #3465fc' : 'black'}"
                density="compact"
            >  
               <div class="text-col-black">Our Industries</div> 
            </v-btn></v-hover>
            
            <!--About Us-->
            <v-hover v-slot="{ hover}"><v-btn
                plain
                @click.prevent="aboutPage"
                class="d-none d-sm-flex"
                :style="{ 'border-bottom': hover ? '5px solid #3465fc' : 'black'}"
                density="compact"
            >  
               <div class="text-col-black">About</div> 
            </v-btn></v-hover>

            <!--Contact Us-->
            <v-hover v-slot="{ hover}"><v-btn
                plain
                @click.prevent="contactUs"
                class="d-none d-sm-flex"
                :style="{ 'border-bottom': hover ? '5px solid #3465fc' : 'black'}"
                density="compact"
            >  
               <div class="text-col-black">Contact Us</div> 
            </v-btn></v-hover>

            <v-col cols="auto" v-if="!isMobileView">
             <v-btn @click.prevent="loginPage" color="primary" density="comfortable"><v-icon>mdi-login-variant</v-icon>Login</v-btn>
            </v-col>
        <!--<Theme />-->  
        <v-menu>
        <template v-slot:activator="{ on, attrs }">       
                <div class="pr-5">
                    <v-app-bar-nav-icon v-bind="attrs"
                        v-on="on"
                        class="d-flex d-sm-none"
                        color="indigo"
                        size="x-large"
                        density="comfortable">
                    </v-app-bar-nav-icon>
               
                </div>
        </template>
       </v-menu>
        </v-app-bar>

        <v-main>
            <router-view />
        </v-main>
    </v-app>
</template>
<style>
    .text-col-black{
        color:black;
        font-size: 40;
        font-weight: bold;
    }
   

</style>

<script>
import Theme from "./general/Theme";
import navdrawer from "./general/Drawermenu";
import searchJob from "./general/searchjob";


export default {
    components: {
        Theme,
        navdrawer,
        searchJob
    },
    data() {
        return {
            isMobileView: false
        };
    },
    mounted(){
        // Check the screen width on component mount and whenever the window is resized
        window.addEventListener('resize', this.checkMobileView);
        this.checkMobileView();
    },
    methods: {
        // Adjust the breakpoint as per your needs
        checkMobileView() {
         this.isMobileView = window.innerWidth <= 768; 
        },
        beforeDestroy() {
        // Remove the event listener when the component is destroyed
         window.removeEventListener('resize', this.checkMobileView);
        },
        loginPage() {
            if(this.$route.name != 'Login') {
                this.$router.push({name: 'Login'});
            }
        },
        aboutPage() {
            if(this.$route.name != 'About') {
                this.$router.push({name: 'About'});
            }
        },
        HomePage() {
            if(this.$route.name != 'Home') {
                this.$router.push({name: 'Home'});
            }
        },
        ClientPage() {
            if(this.$route.name != 'Clients') {
                this.$router.push({name: 'Clients'});
            }
        },
        JobsPage() {
            if(this.$route.name != 'Jobs') {
                this.$router.push({name: 'Jobs'});
            }
        }
    },
}
</script>