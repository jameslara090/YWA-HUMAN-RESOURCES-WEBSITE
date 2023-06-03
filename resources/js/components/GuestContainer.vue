<template>
    <v-app class="v-theme--light">
        <v-app-bar
            app
            dark
            flat
            style="background-color: rgb(231, 240, 246); top: 0px; z-index: 1080; transform: translateY(0%); position: fixed; height: 63px; left: 4px; width: calc((100% - 0px) - 0px);"
            
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
            <v-menu offset-y>

                <template v-slot:activator="{ on, attrs }">
                    <v-btn
                        plain
                        icon
                        v-bind="attrs"
                        v-on="on"
                        class="d-flex d-sm-none"
                    >
                    <v-icon>mdi-dots-vertical</v-icon>
                    </v-btn>
                </template>

                <v-list>
                    <!--Homepage-->
                    <v-list-item
                        @click.prevent="HomePage"
                    >
                        <v-icon left>mdi-check</v-icon>
                        <v-list-item-title>
                            Home
                        </v-list-item-title>
                    </v-list-item>

                    <!--Client Page-->
                    <v-list-item
                        @click.prevent="ClientPage"
                    >
                        <v-icon left>mdi-check</v-icon>
                        <v-list-item-title>
                            Client
                        </v-list-item-title>
                    </v-list-item>

                    <!--Jobs Page-->
                    <v-list-item
                        @click.prevent="JobsPage"
                    >
                        <v-icon left>mdi-check</v-icon>
                        <v-list-item-title>
                            Jobs
                        </v-list-item-title>
                    </v-list-item>

                      <!--Our Industries Page-->
                      <v-list-item
                        @click.prevent="JobsPage"
                    >
                        <v-icon left>mdi-check</v-icon>
                        <v-list-item-title>
                            Our Industries
                        </v-list-item-title>
                    </v-list-item>

                    <!--About Us-->
                    <v-list-item
                        @click.prevent="aboutPage"
                    >
                        <v-icon left>mdi-check</v-icon>
                        <v-list-item-title>
                            About Us
                        </v-list-item-title>
                    </v-list-item>
                     <!--Contact Us-->
                    <v-list-item
                        @click.prevent="changelogsPage"
                    >
                        <v-list-item-title>
                            <v-icon left>mdi-format-list-text</v-icon>
                            Contact Us
                        </v-list-item-title>
                    </v-list-item>
                    <v-list-item
                        @click.prevent="loginPage"
                    >
                        <v-list-item-title>
                            <v-icon left>mdi-login-variant</v-icon>
                            Apply Now
                        </v-list-item-title>
                    </v-list-item>
                </v-list>
            </v-menu>
           
            <!--Homepage-->
            <v-hover v-slot="{ hover}"><v-btn
                plain
                @click.prevent="HomePage"
                class="d-none d-sm-flex"
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

            <v-col cols="auto">
             <v-btn @click.prevent="loginPage" density="comfortable">Apply Now</v-btn>
            </v-col>

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

export default {
    components: {
        Theme,
    },
    methods: {
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