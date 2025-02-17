<script setup>
import { onMounted, ref, watch, reactive, provide } from 'vue'
import axios from 'axios'

import Header from './components/Header.vue'
import CardList from './components/CardList.vue'
import Drawer from './components/Drawer.vue'

const items = ref([])
const filters = reactive({
  sortBy: '',
  searchQuery: '',
})

const onChangeSelect = (event) => {
  filters.sortBy = event.target.value
}

const onChangeSearch = (event) => {
  filters.searchQuery = event.target.value
}

provide('addToFavorite', addToFavorite)

const addToFavorite = async (item) => {
  item.isFavorite = true
}

const fetchItems = async () => {
  try {
    const params = {
      sortBy: filters.sortBy,
    }
    if (filters.searchQuery) {
      params.title = `*${filters.searchQuery}*`
    }
    const { data } = await axios.get(`https://c5d2b31b00abdd63.mokky.dev/items`, { params })
    items.value = data.map((obj) => ({ ...obj, isFavorite: false, isAdded: false }))
  } catch (e) {
    console.log(e)
  }
}

const fetchFavorites = async () => {
  try {
    const { data: favorites } = await axios.get(`https://c5d2b31b00abdd63.mokky.dev/favorites`)
    items.value = items.value.map((item) => {
      const favorite = favorites.find((favorite) => favorite.parentId === item.id)
      if (!favorite) {
        return item
      }
      return {
        ...item,
        isFavorite: true,
        favoriteId: favorite.id,
      }
    })
    console.log(items.value)
  } catch (e) {
    console.log(e)
  }
}

onMounted(async () => {
  await fetchItems()
  await fetchFavorites()
})
watch(filters, async () => {
  await fetchItems()
  await fetchFavorites()
})
</script>

<template>
  <link rel="stylesheet" href="./assets/main.css">
  <body>
    <!--    <Drawer />-->
    <div class="bg-white w-4/5 m-auto rounded-xl mt-14 shadow-xl">
      <Header />
      <div class="p-10">
        <div class="flex justify-between items-center">
          <h2 class="text-3xl font-bold mb-8">Все Кроссовки</h2>
          <div class="flex gap-4">
            <select
              @change="onChangeSelect"
              class="py-2 px-3 border border-gray-200 rounded-md outline-none"
            >
              <option value="title">По названию</option>
              <option value="price">По цене (дешевые)</option>
              <option value="-price">По цене (дорогие)</option>
            </select>
            <div class="relative">
              <img class="absolute left-4 top-3" src="/search.svg" alt="Search" />
              <input
                class="border border-gray-200 rounded-md py-2 pl-11 pr-4 outline-none focus:border-gray-400"
                type="text"
                placeholder="Поиск... "
                @input="onChangeSearch"
              />
            </div>
          </div>
        </div>
        <CardList :items="items" />
      </div>
    </div>
  </body>
</template>
