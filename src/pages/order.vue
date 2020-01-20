<template>
  <v-layout>
    <v-flex v-for="chip in chips" :key="chip.name" class="text-left">
      <v-chip label :class="`${chip.color}--text ${chip.color} lighten-3`">
        {{ chip.name }}
      </v-chip>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  data() {
    return {
      chips: [
        {
          name: "New Order"
        },
        {
          name: "Delivered",
          color: "info"
        },
        {
          name: "Success",
          color: "success"
        },
        {
          name: "Wrong Order",
          color: "warning"
        },
        {
          name: "Canceled",
          color: "error"
        }
      ]
    }
  }
}
</script>
