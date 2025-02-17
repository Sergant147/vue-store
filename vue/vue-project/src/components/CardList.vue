<script setup>
import Card from './Card.vue'

defineProps({
  items: Array,
})

function onClickFavorite() {
  alert('Favorite Card')
}

function onClickAdded() {
  alert('Added Card')
}
</script>
<template>
  <div class="grid grid-cols-4 gap-5">
    <Card
      v-for="item in items"
      :key="item.id"
      :imageUrl="item.imageUrl"
      :title="item.title"
      :price="item.price"
      :on-click-favorite="onClickFavorite"
      :on-click-add="onClickAdded"
      :isFavorite="item.isFavorite"
      :id="item.id"
    />
  </div>
</template>
