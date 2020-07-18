<template>
  <v-card id="card" color="#061422">
    <v-card-title>
      <span id="card-title">{{ $t('CardRoomTime.title') }}</span>
    </v-card-title>
    <v-card-text>
      <v-container>
        <v-row>
          <v-col cols="6" sm="4" md="4" lg="4" xl="4">
            <div id="timepicker">
              <vue-timepicker 
                :placeholder="this.$t('CardRoomTime.infinite')"
                :format="timeFormat" 
                :second-interval="15" 
                :minute-range="[[0,10]]" 
                input-width="150px" 
                minute-label="minutes" 
                second-label="seconds" 
                hide-disabled-minutes 
                v-model="timeData">
              </vue-timepicker>
            </div>
          </v-col>
        </v-row>
      </v-container>
    </v-card-text>
    <v-card-actions id="card-actions">
      <div class="flex-grow-1"></div>
      <v-btn dark depressed color="#FF5252" @click="setTimeLimitation">{{ $t('CardRoomTime.next') }}</v-btn>
      <v-btn dark depressed color="#43B581" @click="cancel">{{ $t('CardRoomTime.cancel') }}</v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
  import VueTimepicker from 'vue2-timepicker/src/vue-timepicker.vue'
  
  export default {
    data() {
      return {
        timeFormat: 'mm:ss',
        timeData: {          
          mm: '',
          ss: '',        
        },
      }
    },
    components: { VueTimepicker },
    methods: {
      setTimeLimitation() {
        // Pass time limitation to parent component
        this.$emit('setTimeLimitation', this.timeData)
      },
      cancel() {
        this.$emit('cancel')
      }
    }
  }
</script>

<style scoped>
#card-title {
  font-size: 16px;
  font-weight: 500;
  color: #ffffff;
  opacity: 0.9;
}
#card {
  min-height: 260px;
}
#card-actions {
  position: relative;
  bottom: -52px;
}
#timepicker {
  /* background-color: #ffffff; */
  font-weight: 700;
  color: #ffffff;
  width: 150px;
}
</style>