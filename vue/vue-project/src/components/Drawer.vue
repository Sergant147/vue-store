<script setup>
import DrawerHead from './DrawerHead.vue'
import CartItemList from './CartItemList.vue'
</script>
<template>
  <div class="fixed top-0 left-0 h-full w-full bg-black z-10 opacity-70"></div>
  <div class="bg-white w-96 h-full fixed right-0 top-0 z-20 p-8">
    <DrawerHead />
    <CartItemList />
    <div class="flex flex-col gap-4 my-7 mt-7">
      <div class="flex gap-2">
        <span>Итого </span>
        <div class="flex-1 border-b border-dashed border-slate-200"></div>
        <b>12990 ₽</b>
      </div>
      <div class="flex gap-2">
        <span>Налог 5%</span>
        <div class="flex-1 border-b border-dashed border-slate-200"></div>
        <b>900 ₽</b>
      </div>
      <button
        class="mt-4 bg-lime-500 transition w-full cursor-pointer disabled:cursor-wait disabled:bg-slate-400 rounded-xl py-3 text-white hover:bg-lime-600 active:bg-lime-700"
      >
        Оформить заказ
      </button>
    </div>
  </div>
</template>
