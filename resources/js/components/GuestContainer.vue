<template>
    <v-app>
        <v-app-bar
            app
            color="light"
            dark
            flat
        >
            <v-toolbar-title>
                <v-img :max-width="300" :max-height="200" src="images/Ywa.png"  lazy-src="images/Ywa.png">
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
            <v-btn
                plain
                dark
                @click.prevent="HomePage"
                class="d-none d-sm-flex"
            >  
                Home
            </v-btn>
            <!--Clients-->
            <v-btn
                plain
                dark
                @click.prevent="ClientPage"
                class="d-none d-sm-flex"
            >
                Clients
            </v-btn>
            <!--Jobs-->
            <v-btn
                plain
                dark
                @click.prevent="JobsPage"
                class="d-none d-sm-flex"
            >
                Jobs
            </v-btn>
            <v-btn
                plain
                dark
                @click.prevent="JobsPage"
                class="d-none d-sm-flex"
            >
                Our Industries
            </v-btn>
            <!--About Us-->
            <v-btn
                plain
                dark
                @click.prevent="aboutPage"
                class="d-none d-sm-flex"
            >
                About Us
            </v-btn>

            <!--Contact Us-->
             <!--About Us-->
             <v-btn
                plain
                dark
                @click.prevent="aboutPage"
                class="d-none d-sm-flex"
            >
                Contact Us
            </v-btn>

            <v-btn
                plain
                dark
                @click.prevent="loginPage"
                class="d-none d-sm-flex"
            >
                <v-icon left>mdi-login-variant</v-icon>
                Apply Now
            </v-btn>

            <Theme />

        </v-app-bar>

        <v-main>
            <router-view />
        </v-main>

    </v-app>
</template>

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