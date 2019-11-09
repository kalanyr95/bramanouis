<template>
  <div class="home">
    <h1>homepage</h1>
    <v-btn class="pink white--text">SIGN</v-btn>
    <v-btn class="hidden-md-and-down">SIGN</v-btn>


    <v-icon large color="teal darken-2">mdi-email</v-icon>
    
    <template>
  <v-card
    class="mx-auto"
    max-width="400"
  >
    <v-img
      class="white--text align-end"
      height="200px"
      src="https://cdn.vuetifyjs.com/images/cards/docks.jpg"
    >
      <v-card-title>Top 10 Australian beaches</v-card-title>
    </v-img>

    <v-card-subtitle class="pb-0">Number 10</v-card-subtitle>

    <v-card-text class="text--primary">
      <div>Whitehaven Beach</div>

      <div>Whitsunday Island, Whitsunday Islands</div>
    </v-card-text>

    <v-card-actions>
      <v-btn
        color="orange"
        text
      >
        Share
      </v-btn>

      <v-btn
        color="orange"
        text
      >
        Explore
      </v-btn>
    </v-card-actions>
  </v-card>
</template>
<div id="app">
  <v-container>
    <v-layout row class="text-xs-center">
      <v-flex xs3 style="background-image: url('http://cdn.wallpapersafari.com/7/86/gqiGH7.jpg')">
        <v-card height="500px"></v-card>
      </v-flex>
      <v-flex xs4 class="grey lighten-4">
        <v-container style="position: relative;top: 13%;" class="text-xs-center">
          <v-card flat>
            <v-card-title primary-title>
              <h4>Login</h4>
            </v-card-title>
            <v-form>
            <v-text-field prepend-icon="person" name="Username" label="Username"></v-text-field>
            <v-text-field prepend-icon="lock" name="Password" label="Password" type="password"></v-text-field>
            <v-card-actions>
              <v-btn primary large block>Login</v-btn>
            </v-card-actions>
            </v-form>
          </v-card>
        </v-container>
      </v-flex>
    </v-layout>
  </v-container>
</div>
  </div>
</template>
<script>
// @ is an alias to /src
export default {

}
</script>

<!--
<template>
  <v-row justify="space-around" align="center" >
    <v-form justify="space-around" align="center"
      ref="form"
      v-model="valid"
    >

    <v-chip
      class="ma-2"
      color="primary"
      outlined
    >
      <h1>Renseignez vos identifiants</h1>
      <v-icon right>mdi-account-key</v-icon>
    </v-chip>

      <v-text-field
        v-model="email"
        :rules="emailRules"
        label="E-mail"
        required
      ></v-text-field>

      <v-text-field
            v-model="password"
            :append-icon="showIcon ? 'mdi-eye' : 'mdi-eye-off'"
            :rules="[passwordrules.required, passwordrules.min]"
            :type="showIcon ? 'text' : 'password'"
            name="input-10-1"
            label="Mot de passe"
            counter
            @click:append="showIcon = !showIcon"
      ></v-text-field>

    <v-chip v-if="failed === true"
      class="ma-2"
      color="red"
      outlined
    >
      <span>{{ failedMessage }}</span>
    </v-chip>

      <v-switch v-model="remenber" class="ma-4" label="Se souvenir de moi"></v-switch>

      <v-btn
        :disabled="!valid"
        color="success"
        class="mr-4"
        @click="login"
      >
        Connexion
      </v-btn>

      <router-link to="/register" class="ma-4">Mot de passe oublié ?</router-link>
    </v-form>
  </v-row>
</template>

<script>

export default {
  data: () => ({
    errorMessage: false,
    valid: true,
    password: '',
    email: '',
    url: 'http://localhost:4000', // 'http://localhost:4000'
    emailRules: [
      v => !!v || 'Le mail est requis.',
      v => /.+@.+\..+/.test(v) || 'Le mail doit être valide.'
    ],
    select: null,
    remenber: true,
    showIcon: false,
    failed: false,
    failedMessage: 'Le nom d\'utilisateur ou le mot de passe est incorrect.',
    passwordrules: {
      required: v => !!v || 'Le mot de passe est requis.',
      min: v => v.length >= 8 || 'Minimum 8 caractères'
    },
    submitted: false
  }),

  methods: {
    login: function () {
      let email = this.email
      let password = this.password
      this.$store.dispatch('login', { email, password })
        .then(response => {
          this.$router.push('/')
          location.reload()
          console.log(response)
        })

        .catch(error => {
          this.failed = true
          console.log(error)
        })
    },
    validate () {
      if (this.$refs.form.validate()) {
        this.snackbar = true
      }
    },
    reset () {
      this.$refs.form.reset()
    }
  }
}
</script> -->

 <!--
<template>
  <v-row justify="space-around" align="center" >
    <v-form justify="space-around" align="center"
      ref="form"
      v-model="valid"
    >

    <v-chip
      class="ma-2"
      color="primary"
      outlined
    >
      <h1>Je crée mon compte :</h1>
      <v-icon right>mdi-account-plus</v-icon>
    </v-chip>

    <v-text-field
        v-model="firstname"
        :counter="30"
        :rules="[firstnamerules.required, firstnamerules.max]"
        label="Prénom"
        required
    ></v-text-field>

    <v-text-field
        v-model="lastname"
        :counter="30"
        :rules="[lastnamerules.required, lastnamerules.max]"
        label="Nom"
        required
    ></v-text-field>

    <v-text-field
        v-model="email"
        :rules="emailRules"
        label="E-mail"
        required
      ></v-text-field>

    <template>
  <v-menu
    ref="menu"
    v-model="menu"
    :close-on-content-click="false"
    transition="scale-transition"
    offset-y
    full-width
    min-width="290px"
  >
    <template v-slot:activator="{ on }">
      <v-text-field
        v-model="computedDateFormattedMomentjs"
        label="Date de naissance"
        prepend-inner-icon='mdi-calendar'
        readonly
        v-on="on"
        :rules="[birthdayrules.required]"
      ></v-text-field>
    </template>
    <v-date-picker
      ref="picker"
      v-model="date"
      locale="fr"
      :max="new Date().toISOString().substr(0, 10)"
      min="1920-01-01"
      :first-day-of-week="1"
      @change="save"
    ></v-date-picker>
  </v-menu>
</template>

<template>
  <v-container fluid>
    <p>Vous êtes : </p>
    <v-radio-group v-model="radios" :mandatory="false"
    :rules="[v => !!v || 'Le genre est requis.']">
      <v-radio label="Une Femme" value="femme"></v-radio>
      <v-radio label="Un Homme" value="homme"></v-radio>
    </v-radio-group>
  </v-container>
</template>

      <v-text-field
            v-model="password"
            :append-icon="showIcon ? 'mdi-eye' : 'mdi-eye-off'"
            :rules="[passwordrules.required, passwordrules.min]"
            :type="showIcon ? 'text' : 'password'"
            name="input-10-1"
            label="Mot de passe"
            counter
            @click:append="showIcon = !showIcon"
      ></v-text-field>

      <v-checkbox
        v-model="checkbox"
        :rules="[v => !!v || 'Vous devez accepter les C.G.U.']"
        label="Accepter les C.G.U."
        required
      ></v-checkbox>

      <core-CGU />

      <v-switch v-model="remenber" class="ma-4" label="Je souhaite qu'on m'informe des nouveautés, cadeaux et bons plans !"></v-switch>

      <v-btn
        :disabled="!valid"
        color="success"
        class="mr-4"
        @click="register"
      >
        Enregistrement
      </v-btn>

      <router-link to="/login" class="ma-4">Déjà membre ? Connectez-vous</router-link>
    </v-form>
  </v-row>
</template>

<script>
import moment from 'moment'
moment.locale('fr')
export default {
  data: () => ({
    firstname: '',
    lastname: '',
    password: '',
    radios: '',
    date: null,
    menu: false,
    valid: true,
    name: '',
    email: '',
    remenber: true,
    emailRules: [
      v => !!v || 'Le mail est requis.',
      v => /.+@.+\..+/.test(v) || 'Le mail doit être valide.'
    ],
    select: null,
    showIcon: false,
    passwordrules: {
      required: v => !!v || 'Le mot de passe est requis.',
      min: v => v.length >= 8 || 'Minimum 8 caractères'
    },
    firstnamerules: {
      required: v => !!v || 'Le prénom est requis.',
      max: v => v.length <= 30 || 'Maximum 30 caractères'
    },
    lastnamerules: {
      required: v => !!v || 'Le nom est requis.',
      max: v => v.length <= 30 || 'Maximum 30 caractères'
    },
    birthdayrules: {
      required: v => !!v || 'La date de naissance est requise.'
    }
  }),

  components: {
    CoreCGU: () => import('@/components/register/CGU')
  },

  watch: {
    menu (val) {
      val && setTimeout(() => (this.$refs.picker.activePicker = 'YEAR'))
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
    save (date) {
      this.$refs.menu.save(date)
    },
    register: function () {
      let data = {
        firstname: this.firstname,
        lastname: this.lastname,
        birthday: this.date,
        gender: this.radios,
        newsletter: this.remenber,
        email: this.email,
        password: this.password
      }
      this.$store.dispatch('register', data)
        .then(() => this.$router.push('/'))
        .catch(err => console.log(err))
    }
  },
  computed: {
    computedDateFormattedMomentjs () {
      return this.date ? moment(this.date).format('dddd, DD MMMM YYYY') : ''
    }
  }
}
</script> -->