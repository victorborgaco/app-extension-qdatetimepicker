<template>
  <q-page class="flex flex-center">
    <div class="full-width row q-pa-md">
      <div class="col col-12 q-pa-md">
        <q-select
            outlined
            v-model="language"
            :options="languages"
            label="Language"
            option-label="nativeName"
            option-value="isoName"
            map-options
            emit-value
            @input="onLanguageInput">
        </q-select>
      </div>
      <div class="col col-md-4 col-12 q-pa-md">
        <q-card>
          <q-card-section>
            <div class="text-h6">Input Types</div>
          </q-card-section>
          <q-separator inset />
          <q-card-section>
            <q-datetime-picker class="q-mb-md" label="Standard Date Picker" v-model="date"></q-datetime-picker>
            <q-datetime-picker class="q-mb-md" outlined label="Outlined Date Picker" v-model="date"></q-datetime-picker>
            <q-datetime-picker class="q-mb-md" filled label="Filled Date Picker" v-model="date"></q-datetime-picker>
            <q-datetime-picker class="q-mb-md" standout label="Standout Date Picker" v-model="date"></q-datetime-picker>
          </q-card-section>
        </q-card>
      </div>
      <div class="col col-md-4 col-12 q-pa-md">
        <q-card dark class="bg-grey-10">
          <q-card-section>
            <div class="text-h6">Dark Mode</div>
          </q-card-section>
          <q-separator dark inset />
          <q-card-section class="">
            <q-datetime-picker class="q-mb-md" outlined label="Date Picker" color="negative" dark v-model="date"></q-datetime-picker>
            <q-datetime-picker class="q-mb-md" outlined label="Time Picker" :time="true" color="negative" dark v-model="time"></q-datetime-picker>
            <q-datetime-picker class="q-mb-md" outlined label="DateTime Picker" :date="true" :time="true" color="negative" dark v-model="datetime"></q-datetime-picker>
            <q-datetime-picker class="q-mb-md" standout label="Standout DateTime Picker" :date="true" :time="true" color="negative" dark v-model="datetime" :format24h="false"></q-datetime-picker>
          </q-card-section>
        </q-card>
      </div>
      <div class="col col-md-4 col-12 q-pa-md">
        <q-card>
          <q-card-section>
            <div class="text-h6">Light Mode</div>
          </q-card-section>
          <q-separator inset />
          <q-card-section>
            <q-datetime-picker class="q-mb-md" outlined label="Date Picker" color="positive" v-model="date"></q-datetime-picker>
            <q-datetime-picker class="q-mb-md" outlined label="Time Picker" :time="true" color="positive" v-model="time"></q-datetime-picker>
            <q-datetime-picker class="q-mb-md" outlined label="DateTime Picker" :date="true" :time="true" color="positive" v-model="datetime"></q-datetime-picker>
            <q-datetime-picker class="q-mb-md" standout label="Standout DateTime Picker" :date="true" :time="true" color="positive" v-model="datetime" :format24h="false"></q-datetime-picker>
          </q-card-section>
        </q-card>
      </div>
      <div class="col col-md-6 col-12 q-pa-md">
        <q-banner rounded class="bg-primary text-white">
          <template v-slot:avatar>
            <q-avatar>
              <img src="https://cdn.quasar-framework.org/logo/svg/quasar-logo.svg">
            </q-avatar>
          </template>
          New to Quasar? Don't miss the chance to know the best Framework based on Vue
          <template v-slot:action>
            <a href="https://v1.quasar-framework.org">
              <q-btn flat color="white" label="Show me" />
            </a>
          </template>
        </q-banner>
      </div>
      <div class="col col-md-6 col-12 q-pa-md">
        <q-banner rounded class="bg-grey-10 text-white">
          <template v-slot:avatar>
            <q-avatar>
              <img src="statics/git-octupus.png">
            </q-avatar>
          </template>
          Quasar App Extension QDatetimePicker Repository
          <template v-slot:action>
            <a href="https://github.com/TobyMosque/app-extension-qdatetimepicker">
              <q-btn flat color="white" label="Show me" />
            </a>
          </template>
        </q-banner>
      </div>
    </div>
  </q-page>
</template>

<style>

</style>

<script>
// import something here
import languages from 'quasar/lang/index.json'
export default {
  name: 'PageIndex',
  data () {
    return {
      date: '2018-11-02',
      time: '15:46',
      datetime: '2018-11-02T15:46',
      language: this.$q.lang.isoName,
      languages
    }
  },
  watch: {
    date: {
      immediate: true,
      handler () {
        console.log('date: ', this.date)
      }
    },
    time: {
      immediate: true,
      handler () {
        console.log('time: ', this.time)
      }
    },
    datetime: {
      immediate: true,
      handler () {
        console.log('datetime: ', this.datetime)
      }
    }
  },
  methods: {
    async onLanguageInput () {
      let lang = await import(`quasar/lang/${this.language}`)
      this.$q.lang.set(lang.default)
    }
  }
}
</script>
