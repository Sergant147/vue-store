<template>
  <header class="flex justify-between border-b border-slate-200 px-10 py-8">
    <div class="flex items-center gap-4">
      <img src="/logo.png" alt="Logo" class="w-10" />
      <div>
        <h2 class="text-xl font-bold uppercase">Vue Sneakers</h2>
        <p class="text-slate-600">Магазин лучших кроссовок</p>
      </div>
    </div>
    <ul class="flex items-center gap-10">
      <li class="flex items-center gap-3 text-gray-500 hover:text-black cursor-pointer">
        <img src="/cart.svg" alt="Cart" />
        <b>1205. руб</b>
      </li>
      <li class="flex items-center gap-3 text-gray-500 cursor-pointer">
        <img class="hover:w-7 hover:h-7" src="/heart.svg" alt="Heart" />
        <span class="hover:text-black">Закладки</span>
      </li>
      <li>
        <div class="flex flex-col">
          <div class="flex justify-around">
            <div class="flex items-center gap-3 text-gray-500 cursor-default">
              <img class="transition hover:w-3 hover:h-3" src="/profile.svg" alt="Heart" />
              <span>Профиль</span>
            </div>
            <div class="py-4">
              <svg
                class="rotate-90"
                width="16"
                height="14"
                viewBox="0 0 16 14"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  d="M1 7H14.7143"
                  stroke="black"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                />
                <path
                  d="M8.71436 1L14.7144 7L8.71436 13"
                  stroke="black"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                />
              </svg>
            </div>
          </div>
          <input class="py-4 h-10 font-bold border" placeholder="Имя... " />
        </div>
      </li>
    </ul>
  </header>
</template>
<script setup lang="ts"></script>
