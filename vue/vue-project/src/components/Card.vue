<script setup>
import { inject } from 'vue'

const props = defineProps({
  id: Number,
  price: Number,
  title: String,
  imageUrl: String,
  onClickAdd: Function,
  onClickFavorite: Function,
  isFavorite: Boolean,
  isAdded: Boolean,
})
const addToFavorite = inject('addToFavorite')
const onClickFavorite = () => {
  const obj = {
    ...props,
    parentId: props.id,
  }
  addToFavorite(obj)
}
</script>
<template>
  <div
    class="relative bg-white border border-slate-100 rounded-3xl p-8 cursor-pointer hover:-translate-y-2 transition hover:shadow-xl"
  >
    <img
      :src="isFavorite ? '/like-1.svg' : '/like-2.svg'"
      alt="Like"
      @click="onClickFavorite"
      class="absolute top-0 left-0"
    />
    <img :src="imageUrl" alt="Sneaker" />
    <p class="mt-2">{{ title }}</p>
    <div class="flex justify-between mt-5">
      <div flex="flex flex-col">
        <span class="text-slate-400">Цена: </span>
        <b>{{ price }}. руб</b>
      </div>
      <img :src="!isAdded ? '/plus.svg' : '/checked.svg'" @click="onClickAdd" alt="Plus" />
    </div>
  </div>
</template>
