<script setup lang="ts">
import vSelect from 'vue-select'
import {ref} from "vue";

const values = ref([])
const options = [
  {id: '1', label: '日本，東京'},
  {id: '2', label: '日本，広島'},
  {id: '3', label: '日本，福岡'},
  {id: '4', label: 'アメリカ，カリフォルニア'},
  {id: '5', label: 'アメリカ，ニューヨーク'},
]
const onSearch = (text: string, loading: (loading: boolean) => void) => {
  loading(true)
  console.log(text)
  loading(false)
}
</script>

<template>
  <v-select class="style-chooser w-full border-0" :options="options" v-model="values" multiple @search="onSearch">
    <template #selected-option-container="{ option, deselect, multiple, disabled }" >
      <div class="bg-blue-200 px-2 py-1 my-1 mr-1 rounded">
        {{option.label}}
        <span class="ml-1 cursor-pointer" @click="deselect(option)">X</span>
      </div>
    </template>
  </v-select>
</template>

<style>
.style-chooser .vs__search::placeholder,
.style-chooser .vs__dropdown-toggle {
  background: #dfe5fb;
  border: none;
  color: #394066;
  text-transform: lowercase;
  font-variant: small-caps;
}

.style-chooser .vs__clear,
.style-chooser .vs__open-indicator {
  fill: #394066;
}
</style>
