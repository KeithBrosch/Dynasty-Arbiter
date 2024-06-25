<script setup lang="ts">
import supabase from '../utlis/supabaseClient.js'

let ktcValues = []
let fcValues = []

const getKTCPlayerValues = async function () {
  const { data, error } = await supabase.from(import.meta.env.VITE_SUPABASE_KTC_DB_NAME).select()

  if (error) console.error(error)
  if (data) this.ktcValues = data
}

const getFCPlayerValues = async function () {
  const { data, error } = await supabase.from(import.meta.env.VITE_SUPABASE_FC_DB_NAME).select()

  if (error) console.error(error)
  if (data) this.fcValues = data
}

getKTCPlayerValues()
getFCPlayerValues()
</script>

<template>
  <h1>Player Rankings</h1>
  {{ ktc_values }}
  <br />
  {{ fc_values }}
</template>
