<script setup lang="ts">
import { PhHeart } from "@phosphor-icons/vue";
import jsonPayload from "./data/texts.json";

const data: Data = {
  Names: jsonPayload['nomes'],
  Declarations: jsonPayload['declaracoes'],
  Moments: jsonPayload['momentos'].map(m => {
    return {
      src: m['src'],
      text: m['texto'],
    }
  }),
};
const randIdxName: number = ~~(Math.random() * data.Names.length);
const randIdxMoment: number = ~~(Math.random() * data.Moments.length);
const randIdxDeclaration: number = ~~(Math.random() * data.Declarations.length);
</script>

<template>
  <main class="font-roboto w-full min-h-screen flex justify-center items-center sm:px-8 sm:py-16 px-0 py-8">
    <section id="main_window"
      class="bg-cyan-50 px-8 sm:max-w-3xl w-full h-full py-4 sm:px-16 sm:py-8 sm:rounded-xl drop-shadow-xl shadow-xl flex justify-center items-center flex-col gap-8">
      <div id="window_head" class="flex flex-col gap-2 justify-center items-center">
        <div class="text-5xl flex flex-row flex-nowrap gap-2 justify-center items-center">
          <PhHeart weight="fill" />
          <h1 class="font-tangerine text-5xl font-bold text-center">
            Para meu amor <span class="text-red-900">Ana Carolina</span>
          </h1>
          <PhHeart weight="fill" />
        </div>
        <div>
          <p class="font-tangerine text-3xl font-bold text-gray-500 text-center">"
            {{ data.Declarations[randIdxDeclaration] }}"
          </p>
          <p class="font-tangerine text-3xl font-bold text-gray-500 text-end">
            - {{ data.Names[randIdxName] }}
          </p>
        </div>
      </div>
      <div id="window_image"
        class="flex flex-col sm:flex-row flex-nowrap gap-4 drop-shadow-xl shadow-xl rounded-lg justify-center items-center max-w-96 sm:max-w-none">
        <img :src="data.Moments[randIdxMoment].src" alt="Meu amor"
          class="sm:max-h-96 object-contain border-1 rounded-tl-xl rounded-tr-xl sm:rounded-bl-xl sm:rounded-tr-none border-gray-500">
        <div class="w-full h-full flex justify-center items-center p-8">
          <p id="image_moment" class="font-tangerine text-3xl text-center font-bold">
            {{ data.Moments[randIdxMoment].text }}
          </p>
        </div>
      </div>
    </section>
  </main>
</template>

<style scoped></style>
