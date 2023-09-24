<template>
    <div class="flex flex-col justify-between h-[60vh] border min-w-[300px] p-3 shadow-lg rounded-xl">
      <form id="myForm" class="flex flex-col justify-between h-full" @submit.prevent="submit">
        <div class="flex flex-col gap-3">
          <section class="flex flex-col">
            <input required oninvalid="this.setCustomValidity('To pole jest wymagane')" oninput="this.setCustomValidity('')" type="text" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" name="name" placeholder="Imie" />
          </section>
          <section class="flex flex-col">
            <input required oninvalid="this.setCustomValidity('To pole jest wymagane')"  oninput="this.setCustomValidity('')" type="text" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" name="lastname" placeholder="Nazwisko" />
          </section>
          <section class="flex flex-col">
            <input required pattern="^\d{10}$" oninvalid="this.setCustomValidity('NIP musi składać się z 10 cyfr')"  oninput="this.setCustomValidity('')" type="text" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" name="nip" placeholder="NIP" />
          </section>
          <section class="flex flex-col">
            <input required oninvalid="this.setCustomValidity('To pole jest wymagane')"  oninput="this.setCustomValidity('')" type="text" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" name="phonenr" placeholder="Numer telefonu" />
          </section>
          <section class="flex flex-col">
            <input required pattern="^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$" oninvalid="this.setCustomValidity('Hasło musi miec minimum 8 znaków, zawierać znaki specjalne, cyfrę oraz małe i duże litery')"  oninput="this.setCustomValidity('')" type="password" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" name="passwd" placeholder="Hasło" />
          </section>
          <section class="flex flex-col">
            <input required oninvalid="this.setCustomValidity('To pole jest wymagane')"  oninput="this.setCustomValidity('')" type="text" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" name="address" placeholder="Adres" />
          </section>
          <section class="flex flex-col">
            <input required oninvalid="this.setCustomValidity('To pole jest wymagane')"  oninput="this.setCustomValidity('')" type="text" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" name="address2" placeholder="Adres2" />
          </section>
          <section class="flex flex-col">
            <input required oninvalid="this.setCustomValidity('Proszę podać poprawny adres email')"  oninput="this.setCustomValidity('')" type="email" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" name="email" placeholder="Email" />
          </section>
        </div>
        <div class="flex flex-row justify-between">
          <button class="min-w-[100px] p-3 bg-lime-400 rounded-xl" type="submit" >Zapisz</button>
          <button @click="reset" class="min-w-[100px] p-3 border rounded-xl" type="button" >Reset</button>
        </div>
      </form>
      
    </div>
</template>


<script setup lang="ts">

  import PersonalModalWindow from "./PersonModalWindow.vue";
  import type {PersonInfo} from "../assets/types"
  import useModalStore from "../stores/useModalStore";
  import { markRaw } from "vue";

  const store = useModalStore();  

  function submit(payload: Event){
    const event = payload.currentTarget as HTMLFormElement
    const data = Object.fromEntries(new FormData(event)) as PersonInfo
    store.openModal({ component: markRaw(PersonalModalWindow) , props: {data: data}})
    reset()
  }

  function reset(){
    const form  = document.getElementById("myForm") as HTMLFormElement;
    form.reset()
  }

</script>
