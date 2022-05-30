<script setup>
import {ref, computed } from "vue"

let hexInput = ref("")
let binaryWithPos = ref("")

const convertHex2BinaryWithPos = () => {
    // from hex to a binary representation.
    let result = parseInt(hexInput.value, 16).toString(2)
    let length = result.length
    let convertResult = ""
    // to a format bPos:1,bPos,0 style string.
    for (let pos = 0; pos < length; pos++) {
        convertResult = convertResult + "@" + (length - 1 - pos) +":"+result[pos] + ","
    }
    binaryWithPos.value = "[" + convertResult + "]"
}

</script>

<template>
  <header class="container mx-auto pt-8">
    <h1 class="font-mono text-xl"> Online convertor for programmer focused on networking. </h1>
  </header>
<div class="container mx-auto pt-20">
  <p class="font-mono text-lg">Hex2binary with bit position is: </p>
  <p class="font-mono text-lg text-red-500 break-all">{{ binaryWithPos }}</p>
  <input class="rounded-lg font-mono test-lg" v-model="hexInput" placeholder="Input hex number" @keyup="convertHex2BinaryWithPos" />
</div>
</template>

<style>
@import '@/assets/base.css';
</style>
