<template>
    <div class="flex flex-col items-center w-[500px] h-[500px] rounded-xl bg-white shadow-xl">
      <div class="flex justify-end mt-1 mr-1 self-end"><ModalButton/></div>
      <div class="text-2xl flex justify-center font-size-[12px] font-bond">Informacje personalne</div>
      <div class="mt-10 min-w-[90%] grid grid-cols-2  gap-5">
        <section class="bg-gray-100 rounded-xl p-1">
          <p class="text-md">Imię:</p>
          <span class="font-bold text-gray-500 text-xl">{{ data.name }}</span>
        </section>
        <section class="bg-gray-100 rounded-xl p-1">
          <p class="text-md">Nazwisko:</p>
          <span class="font-bold text-gray-500 text-xl">{{ data.lastname }}</span>
        </section>
        <section class="bg-gray-100 rounded-xl p-1">
          <p class="text-md">NIP:</p>
          <span class="font-bold text-gray-500 text-xl">{{ data.nip }}</span>
        </section>
        <section class="bg-gray-100 rounded-xl p-1">
          <p class="text-md">Numer Telefonu:</p>
          <span class="font-bold text-gray-500 text-xl">{{ data.phonenr }}</span>
        </section>
        <section class="bg-gray-100 rounded-xl p-1">
          <p class="text-md">Adres:</p>
          <span class="font-bold text-gray-500 text-xl">{{ data.address }}</span>
        </section>
        <section class="bg-gray-100 rounded-xl p-1">
          <p class="text-md">Adres2:</p>
          <span class="font-bold text-gray-500 text-xl">{{ data.address2 }}</span>
        </section>
        <section class="bg-gray-100 rounded-xl p-1">
          <p class="text-md">Email:</p>
          <span class="font-bold text-gray-500 text-xl">{{ data.email }}</span>
        </section>
        
      </div>
    </div>
  </template>
  
<script setup lang="ts">
  import ModalButton from "./ModalCloseButton.vue"
  import type {PersonInfo} from "../assets/types"
  defineProps<{ data: PersonInfo }>();
</script>