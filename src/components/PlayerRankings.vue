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
    ktcValues.value = data
  }
}

const getFCPlayerValues = async function () {
  const { data, error } = await supabase.from(import.meta.env.VITE_SUPABASE_FC_DB_NAME).select('*')

  if (error) console.error(error)
  if (data) {
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
