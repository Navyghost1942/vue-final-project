<script setup>
  import { ref } from 'vue'
  import { faker } from '@faker-js/faker'

  import useAPI from '@/composables/useAPI'
  //const { getCoffees } = useAPI()

  const selectCard = () => {
    console.log(`${props.coffee.name} selected`)
  }

  const props = defineProps({
    coffee: {
      type: Object,
      required: true,
      default: () => {
        return {
          coffeeId: '123',
          name: 'John Doe',
          image: 'https://www.example.com'
        }
      },
    },
  })

  //const departmentResponse = await getDepartment(props.coffee.departmentId)
  //const department = ref(departmentResponse)
</script>

<template>
  <RouterLink v-if="props.coffee.coffeeId" :to="`/api/coffees/${props.coffee.coffeeId}`">
  <div class="card" @click="selectCard">
    <div class="card-image">
      <img :src="props.coffee.image" alt="" srcset="" />
    </div>
    <div class="card-details">
      <p class="card-details-name font-poppins">{{ props.coffee.name }}</p>

    </div>
  </div>
  </RouterLink>
</template>

<style scoped lang="postcss">
  .card {
    @apply cursor-pointer overflow-hidden rounded-md p-8 shadow-md transition-transform duration-300 hover:scale-110 hover:shadow-2xl hover:shadow-slate-900;
    &-image {
      img {
        @apply mx-auto rounded-full object-contain;
      }
    }
    &-details {
      @apply flex flex-col gap-2  pt-6 text-center;
      &-name {
        @apply text-4xl  text-black;
      }
      &-job {
        @apply -mt-2 text-xs font-bold text-yellow-700;
      }
      &-quote {
        @apply pt-4 text-lg italic text-slate-800;
      }
    }
  }
</style>