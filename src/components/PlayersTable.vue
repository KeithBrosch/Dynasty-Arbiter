<script setup>
import { defineProps, computed, ref } from 'vue'

const props = defineProps(['ktcValues', 'fcValues'])

const sortAttribute = ref('diff')

const combinedPlayerObjects = computed(() => {
  let combinedArray = []
  // Merge objects from array1 with matching objects from ktcValues
  props.fcValues.forEach((obj1) => {
    let obj2 = props.ktcValues.find((obj2) => obj1.fc_player_name === obj2.ktc_player_name)
    combinedArray.push({
      ...obj1,
      ...(obj2 || {
        // Use empty object if obj2 is null (no match found)
        id: null,
        ktc_created_at: null,
        ktc_player_name: obj1.fc_player_name,
        ktc_player_age: obj1.fc_player_age,
        ktc_player_value: 0,
        ktc_player_slug: null
      })
    })
  })

  // Add objects from ktcValues that are not in fcValues
  props.ktcValues.forEach((obj2) => {
    let obj1 = props.fcValues.find((obj1) => obj1.fc_player_name === obj2.ktc_player_name)
    if (!obj1) {
      combinedArray.push({
        id: null,
        fc_created_at: null,
        fc_player_name: obj2.ktc_player_name,
        fc_player_age: obj2.ktc_player_age,
        fc_player_value: 0,
        fc_player_slug: null,
        ...obj2
      })
    }
  })

  combinedArray.forEach((player) => {
    player.diff = player.ktc_player_value - player.fc_player_value
  })

  // filter out draft picks
  combinedArray = combinedArray.filter(
    (player) =>
      player.fc_player_age !== '' &&
      player.ktc_player_age !== '' &&
      player.ktc_player_age !== 'PICK'
  )

  return combinedArray.sort((a, b) =>
    a[sortAttribute.value] > b[sortAttribute.value]
      ? 1
      : b[sortAttribute.value] > a[sortAttribute.value]
        ? -1
        : 0
  )
})
</script>

<template>
  <table class="players-table">
    <tr>
      <th>Name</th>
      <th>Age</th>
      <th>KTC Value</th>
      <th>FC Value</th>
      <th>Diff</th>
    </tr>
    <tr v-for="player in combinedPlayerObjects" :key="player.player_id">
      <td>{{ player.fc_player_name || player.ktc_player_name }}</td>
      <td>{{ player.fc_player_age || player.ktc_player_age }}</td>
      <td>{{ player.ktc_player_value || 0 }}</td>
      <td>{{ player.fc_player_value || 0 }}</td>
      <td>{{ player.diff }}</td>
    </tr>
  </table>
</template>

<style lang="scss" scoped>
table {
  box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
  width: 100%;
  border-collapse: collapse;
  th,
  td {
    padding: 5px 10px;
    border: 1px solid black;
  }
  th {
    background: #ff7eee;
  }
}
</style>
