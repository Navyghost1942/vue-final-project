<script setup>
  import { onMounted } from 'vue'

  import MainSearch from '@/components/MainSearch.vue'
  import MainCards from '@/components/Maincards.vue'
  import MainPagination from '@/components/MainPagination.vue'

  import useAPI from '@/composables/useAPI'

  const { getCoffees, loading } = useAPI()

  onMounted(async () => {
    await getCoffees()
  })
</script>

<template>
  <p v-if="loading">Loading...</p>
  <div v-else class="wrapper">
    <!--<MainSearch />-->
    <MainCards />
    <MainPagination />
  </div>
</template>

<style scoped lang="postcss">
  .wrapper {
    @apply container mx-auto flex flex-col gap-4 py-4;
  }
</style>
