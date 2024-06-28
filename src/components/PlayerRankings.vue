<script setup lang="ts">
import supabase from '../utlis/supabaseClient.js'
import { ref, inject } from 'vue'
import PlayersTable from './PlayersTable.vue'

const isLoading = ref(true)
const $loading = inject('$loading')
const loader = $loading.show()

let ktcValues = ref([])
let fcValues = ref([])

const getKTCPlayerValues = async function () {
  const { data, error } = await supabase.from(import.meta.env.VITE_SUPABASE_KTC_DB_NAME).select('*')

  if (error) console.error(error)
  if (data) {
    // manipulate player names to make matching easier later
    data.forEach((player) => {
      player.ktc_player_name = player.ktc_player_name.replace('Jr.', '')
      player.ktc_player_name = player.ktc_player_name.replace('III', '')
      player.ktc_player_name = player.ktc_player_name.replace('Gabriel Davis', 'Gabe Davis')
      player.ktc_player_name = player.ktc_player_name.replace('Joshua Palmer', 'Josh Palmer')
      player.ktc_player_name = player.ktc_player_name.replace('D.J. Moore', 'DJ Moore')
      player.ktc_player_name = player.ktc_player_name.replace('D.J. Chark', 'DJ Chark')
      player.ktc_player_name = player.ktc_player_name.replace('Hollywood Brown', 'Marquise Brown')
      player.ktc_player_name = player.ktc_player_name.replace(
        'Marvin Harrison Jr',
        'Marvin Harrison'
      )
    })
    ktcValues.value = data
  }
}

const getFCPlayerValues = async function () {
  const { data, error } = await supabase.from(import.meta.env.VITE_SUPABASE_FC_DB_NAME).select('*')

  if (error) console.error(error)
  if (data) {
    // manipulate player names to make matching easier later
    data.forEach((player) => {
      player.fc_player_name = player.fc_player_name.replace('Jr.', '')
      player.fc_player_name = player.fc_player_name.replace('III', '')
      player.fc_player_name = player.fc_player_name.replace('Gabriel Davis', 'Gabe Davis')
      player.fc_player_name = player.fc_player_name.replace('Joshua Palmer', 'Josh Palmer')
      player.fc_player_name = player.fc_player_name.replace('D.J. Moore', 'DJ Moore')
      player.fc_player_name = player.fc_player_name.replace('D.J. Chark', 'DJ Chark')
      player.fc_player_name = player.fc_player_name.replace('Hollywood Brown', 'Marquise Brown')
      player.fc_player_name = player.fc_player_name.replace('Marvin Harrison Jr', 'Marvin Harrison')
    })
    fcValues.value = data
  }
}

// todo: add loading overlay
getKTCPlayerValues()
getFCPlayerValues()
loader.hide()
isLoading.value = false
</script>

<template>
  <h1>Player Rankings</h1>
  <PlayersTable
    v-show="fcValues.length && ktcValues.length && !isLoading"
    :ktcValues="ktcValues"
    :fcValues="fcValues"
  />
</template>

<style lang="scss" scoped>
h1 {
  text-align: center;
  margin-bottom: 50px;
}
</style>
