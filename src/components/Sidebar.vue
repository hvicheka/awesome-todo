<template>
  <q-item
    clickable
    :to="link"
    class="text-grey-4"
  >
    <q-item-section
      v-if="icon"
      avatar
    >
      <q-icon :name="icon"/>
    </q-item-section>

    <q-item-section>
      {{ title }}
    </q-item-section>
  </q-item>
</template>

<script>
export default {
  name: 'Sidebar',
  props: {
    title: {
      type: String,
      required: true
    },

    link: {
      type: String,
      default: '#'
    },

    icon: {
      type: String,
      default: ''
    }
  }
}
</script>

<style>
.q-drawer .q-router-link--exact-active {
  /*background-color: #F5F5F5 !important;*/
  color: white !important;
}
</style>
