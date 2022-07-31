<template>
  <span @click="goDetail">{{ zen }}</span>
</template>

<script setup>
import { ref, useContext, useFetch, useRouter } from "@nuxtjs/composition-api"

const { $axios } = useContext();
const zen = ref("")

useFetch(async () => {
  const response = await $axios.get("https://api.github.com/zen")
  zen.value = response.data
})

// Commnet out belows to works!!!
const router = useRouter()
const goDetail = () => {
  router.push('/detail')
}
</script>
