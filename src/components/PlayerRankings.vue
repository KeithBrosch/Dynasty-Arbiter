<script setup lang="ts">
import supabase from '../utlis/supabaseClient.js'
import { ref, inject } from 'vue'

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
  <div v-show="fcValues.length && ktcValues.length && !isLoading" class="columns">
    <p>
      <h3>KTC Rankings</h3>
      {{ ktcValues }}
    </p>
    <p>
      <h3>FC Rankings</h3>
      {{ fcValues }}
    </p>
  </div>
</template>

<style lang="scss" scoped>
h1 {
  text-align: center;
  margin-bottom: 50px;
}
.columns {
  display: flex;
  gap: 50px;
}
</style>
