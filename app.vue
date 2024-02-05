<template>
  <div>
    <div ref="pdfSection">
      Thanks for testing out nuxt-pdf!<br>
      <img src="./1.png" alt="image" />
      <ContentDoc path="/pokus" />
    </div>
    <button @click="klik">
      print card
    </button>
  </div>
</template>

<script setup lang="ts">
//Pozn. Export do pdf nebere některé české znaky: ě, č, ř

import { ref } from 'vue'
import { exportToPDF } from '#imports'

const pdfSection = ref<HTMLElement | null>(null)

const DOCUMENT_OPTIONS = {orientation: "p", format: "a5"}
const HTML_OPTIONS = {x: 10, y: 10}

function klik() {
  exportToPDF('my-pdf-file.pdf', pdfSection.value, DOCUMENT_OPTIONS)
  //exportToPDF('my-pdf-file.pdf', pdfSection.value, DOCUMENT_OPTIONS, HTML_OPTIONS)  //Pozn. Toto funguje, ale pouze pro první export do pdf. Druhý export do pdf je prázdný.
}
</script>