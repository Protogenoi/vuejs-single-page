<template>
  <div id="App">
    <v-app light>
      <v-toolbar class="white">
        <v-toolbar-title v-text="title"></v-toolbar-title>
        <v-spacer></v-spacer>
        <v-toolbar-items class="hidden-sm-and-down">
          <v-btn flat>Link One</v-btn>
          <v-btn flat>Link Two</v-btn>
          <v-btn flat>Link Three</v-btn>
        </v-toolbar-items>
      </v-toolbar>

      <v-content>

        <section>
          <v-parallax v-bind:src="paralax" height="600">
            <v-layout
                    column
                    align-center
                    justify-center
                    class="white--text"
            >
              <img v-bind:src="paralaxLogo" alt="Vuetify.js" height="200">
              <h1 class="white--text mb-2 display-1 text-xs-center">ADL</h1>
              <div class="subheading mb-3 text-xs-center">Powered by Vuetify</div>
              <v-btn
                      class="blue lighten-2 mt-5"
                      dark
                      large
                      href="/pre-made-themes"
              >
                Get Started
              </v-btn>
            </v-layout>
          </v-parallax>
        </section>

        <section>
          <v-layout
                  column
                  wrap
                  class="my-5"
                  align-center
          >
            <v-flex xs12 sm4 class="my-3">
              <div class="text-xs-center">
                <h2 class="headline">The best way to start developing</h2>
                <span class="subheading">
                Cras facilisis mi vitae nunc
              </span>
              </div>
            </v-flex>

            <v-flex xs12>
              <v-container grid-list-xl>
                <v-layout row wrap align-center>

                    <v-flex xs12 md6>
                        <v-card class="elevation-0 transparent">
                            <v-card-text class="text-xs-center">
                                <v-icon x-large class="blue--text text--lighten-2">cloud_queue</v-icon>
                            </v-card-text>
                            <v-card-text>
                                <v-list three-line class="tile">
                                    <template v-for="(item, index) in adlFeatures">
                                        <v-subheader
                                                v-if="item.header"
                                                :key="item.header"
                                        >
                                            {{ item.header }}
                                        </v-subheader>

                                        <v-divider
                                                v-if="item.divider"
                                                :key="index"
                                                :inset="item.inset"
                                        ></v-divider>

                                        <v-list-tile
                                                v-else
                                                :key="item.title"
                                                avatar
                                        >
                                            <v-list-tile-avatar>
                                                <img :src="item.avatar">
                                            </v-list-tile-avatar>

                                            <v-list-tile-content>
                                                <v-list-tile-title v-html="item.title"></v-list-tile-title>
                                                <v-list-tile-sub-title v-html="item.subtitle"></v-list-tile-sub-title>
                                            </v-list-tile-content>
                                        </v-list-tile>
                                    </template>
                                </v-list>
                            </v-card-text>
                        </v-card>
                    </v-flex>

                  <v-flex xs12 md6>
                    <v-card class="elevation-0 transparent">
                      <v-card-text class="text-xs-center">
                        <v-icon x-large class="blue--text text--lighten-2">code</v-icon>
                      </v-card-text>
                      <v-card-text>
                          <v-list three-line class="tile">
                              <template v-for="(item, index) in progLangs">
                                  <v-subheader
                                          v-if="item.header"
                                          :key="item.header"
                                  >
                                      {{ item.header }}
                                  </v-subheader>

                                  <v-divider
                                          v-if="item.divider"
                                          :key="index"
                                          :inset="item.inset"
                                  ></v-divider>

                                  <v-list-tile
                                          v-else
                                          :key="item.title"
                                          avatar
                                  >
                                      <v-list-tile-avatar>
                                          <img :src="item.avatar">
                                      </v-list-tile-avatar>

                                      <v-list-tile-content>
                                          <v-list-tile-title v-html="item.title"></v-list-tile-title>
                                          <v-list-tile-sub-title v-html="item.subtitle"></v-list-tile-sub-title>
                                      </v-list-tile-content>
                                  </v-list-tile>
                              </template>
                          </v-list>
                      </v-card-text>
                    </v-card>
                  </v-flex>

                </v-layout>
              </v-container>
            </v-flex>
          </v-layout>
        </section>

        <section>
          <v-parallax v-bind:src="paralaxTwo" height="380">
            <v-layout column align-center justify-center>
              <div class="headline white--text mb-3 text-xs-center">Web development has never been easier</div>
              <em>Kick-start your application today</em>
                <v-dialog v-model="dialog" persistent max-width="600px">
                    <template v-slot:activator="{ on }">
                        <v-btn
                                color="primary"
                                dark
                                v-on="on"
                                class="blue lighten-2 mt-5"
                                large
                        >Open Dialog</v-btn>
                    </template>

                    <v-card>
                        <v-card-title>
                            <span class="headline">App request</span>
                        </v-card-title>
                        <v-card-text>
                            <v-container grid-list-md>
                                <v-layout wrap>
                                    <v-form
                                            ref="form"
                                            v-model="valid"
                                            lazy-validation
                                            >
                                    <v-flex xs12 sm6 md12>
                                        <v-text-field
                                                label="Your name*"
                                                required
                                                v-model="name"
                                                :rules="nameRules"
                                        ></v-text-field>
                                    </v-flex>
                                    <v-flex xs12 sm6 md12>
                                        <v-text-field
                                                label="Mobile*"
                                                persistent-hint
                                                required
                                                v-model="mobile"
                                                :rules="mobileRules"
                                        ></v-text-field>
                                    </v-flex>
                                    <v-flex xs12>
                                        <v-text-field
                                                label="Email*"
                                                required
                                                v-model="email"
                                                :rules="emailRules"
                                        ></v-text-field>
                                    </v-flex>
                                    <v-flex xs12 sm6>
                                        <v-select
                                                v-model="select"
                                                :items="users"
                                                :rules="[v => !!v || 'Select how many users will be using the app']"
                                                label="Users"
                                                required
                                        ></v-select>
                                    </v-flex>
                                    <v-flex xs12 sm6>
                                        <v-select
                                                v-model="languagesSelect"
                                                :items="languages"
                                                label="Languages"
                                                :rules="[v => !!v || 'Pick programming language']"
                                                required
                                        ></v-select>
                                    </v-flex>
                                        <v-btn
                                                :disabled="!valid"
                                                color="success"
                                                @click="validate"
                                        >
                                            Validate
                                        </v-btn>

                                        <v-btn
                                                color="error"
                                                @click="reset"
                                        >
                                            Reset Form
                                        </v-btn>

                                        <v-btn
                                                color="warning"
                                                @click="resetValidation"
                                        >
                                            Reset Validation
                                        </v-btn>
                                    </v-form>
                                </v-layout>
                            </v-container>
                            <small>*indicates required field</small>
                        </v-card-text>
                        <v-card-actions>
                            <v-spacer></v-spacer>
                            <v-btn color="blue darken-1" flat @click="dialog = false">Close</v-btn>
                        </v-card-actions>
                    </v-card>
                </v-dialog>
            </v-layout>
          </v-parallax>
        </section>

        <section>
          <v-container grid-list-xl>
            <v-layout row wrap justify-center class="my-5">
              <v-flex xs12 sm4>
                <v-card class="elevation-0 transparent">
                  <v-card-title primary-title class="layout justify-center">
                    <div class="headline">Company info</div>
                  </v-card-title>
                  <v-card-text>
                    Cras facilisis mi vitae nunc lobortis pharetra. Nulla volutpat tincidunt ornare.
                    Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas.
                    Nullam in aliquet odio. Aliquam eu est vitae tellus bibendum tincidunt. Suspendisse potenti.
                  </v-card-text>
                </v-card>
              </v-flex>
              <v-flex xs12 sm4 offset-sm1>
                <v-card class="elevation-0 transparent">
                  <v-card-title primary-title class="layout justify-center">
                    <div class="headline">Contact us</div>
                  </v-card-title>
                  <v-card-text>
                    Cras facilisis mi vitae nunc lobortis pharetra. Nulla volutpat tincidunt ornare.
                  </v-card-text>
                  <v-list class="transparent">
                    <v-list-tile>
                      <v-list-tile-action>
                        <v-icon class="blue--text text--lighten-2">phone</v-icon>
                      </v-list-tile-action>
                      <v-list-tile-content>
                        <v-list-tile-title>+44 7401 434 619</v-list-tile-title>
                      </v-list-tile-content>
                    </v-list-tile>
                    <v-list-tile>
                      <v-list-tile-action>
                        <v-icon class="blue--text text--lighten-2">place</v-icon>
                      </v-list-tile-action>
                      <v-list-tile-content>
                        <v-list-tile-title>Swansea, Wales</v-list-tile-title>
                      </v-list-tile-content>
                    </v-list-tile>
                    <v-list-tile>
                      <v-list-tile-action>
                        <v-icon class="blue--text text--lighten-2">email</v-icon>
                      </v-list-tile-action>
                      <v-list-tile-content>
                        <v-list-tile-title>michael@adl-crm.uk</v-list-tile-title>
                      </v-list-tile-content>
                    </v-list-tile>
                  </v-list>
                </v-card>
              </v-flex>
            </v-layout>
          </v-container>
        </section>

       <app-footer/>

      </v-content>
    </v-app>
  </div>
</template>

<script>

  import appFooter from './components/Footer/Footer'

export default {
  name: 'App',
  components: {
    appFooter
  },
  data () {
    return {
      dialog: false,
      languagesSelect: null,
      languages: ['PHP', 'Vuejs', 'Python', 'JavaScript'],
      name: '',
      nameRules: [
        v => !!v || 'Name is required'
      ],
      mobileRules: [
        v => !!v || 'Contact number required'
      ],
      email: '',
      emailRules: [
        v => !!v || 'E-mail is required',
        v => /.+@.+/.test(v) || 'E-mail must be valid'
      ],
      select: null,
      users: [
        '1 - 5',
        '6 - 10',
        '11 - 14',
        '15+'
      ],
      title: 'ADL with Vuejs',
      paralaxLogo: require('./assets/vuetify.png'),
      paralax: require('./assets/hero.jpeg'),
      paralaxTwo: require('./assets/section.jpg'),
      progLangs: [
        {
          avatar: require('./assets/vuetify.png'),
          title: 'Vuejs',
          subtitle: "<span class='text--primary'>Vuejs</span> &mdash; The Progressive JavaScript Framework."
        },
        { divider: true, inset: true },
        {
          avatar: require('./assets/icons/javaScriptIcon.png'),
          title: 'JavaScript',
          subtitle: "<span class='text--primary'>JavaScript</span> &mdash; High-level, interpreted programming language."
        },
        { divider: true, inset: true },
        {
          avatar: require('./assets/icons/pythonIcon.jpeg'),
          title: 'Python',
          subtitle: "<span class='text--primary'>Python</span> &mdash; An interpreted, high-level, general-purpose programming language."
        },
        { divider: true, inset: true },
        {
          avatar: require('./assets/icons/phpIcon.png'),
          title: 'PHP',
          subtitle: "<span class='text--primary'>PHP</span> &mdash; Hypertext Preprocessor is a general-purpose programming."
        }
      ],
      adlFeatures: [
        {
          avatar: require('./assets/icons/twilioIcon.png'),
          title: 'Twilio',
          subtitle: "<span class='text--primary'>Twilio</span> &mdash; Cloud communications platform for building SMS, Voice & Messaging applications on an API built for global scale."
        },
        { divider: true, inset: true },
        {
          avatar: require('./assets/icons/sendGridIcon.png'),
          title: 'SendGrid',
          subtitle: "<span class='text--primary'>SendGrid</span> &mdash; Transactional and marketing emails through the world's largest cloud-based email delivery platform."
        },
        { divider: true, inset: true },
        {
          avatar: require('./assets/icons/whatsAppIcon.png'),
          title: 'WhatsApp',
          subtitle: "<span class='text--primary'>WhatsApp</span> &mdash; Send and receive WhatsApp messages globally with API."
        },
        { divider: true, inset: true },
        {
          avatar: require('./assets/icons/googleIcon.png'),
          title: 'Google API',
          subtitle: "<span class='text--primary'>Google API</span> &mdash; Build, deploy, and scale applications, websites, and services on the same infrastructure as Google."
        },
      ]
    }
  },
  methods: {
    validate () {
      if (this.$refs.form.validate()) {
        this.snackbar = true
      }
    },
    reset () {
      this.$refs.form.reset()
    },
    resetValidation () {
      this.$refs.form.resetValidation()
    }
  }
}
</script>

<style scoped>
    .tile {
        background-color: transparent;
    }
</style>
