<template>
  <div class="container">
    <button 
      type="btn" 
      class="add-word-btn btn btn-success"
      @click="add_new_word()"
    >
      Add word
    </button>
    <div class="text-center">
      <SearchWords :words="words"/>
    </div>
  </div>
</template>


<script>

import SearchWords from './components/SearchWords.vue'

export default {
  name: 'App',

  components: {
    SearchWords
  },

  data() {
    return {
      words: ['Макс', 'Даниил', 'Данила', 'Егор', 'Мариша']
    }
  },

  methods: {
    add_new_word() {
      const new_word = prompt("Введите новое слово: ");
      
      if (!new_word) return;

      this.words.push(new_word);
    
    }
  }
}

</script>


<style>

.add-word-btn {
  top: 0.3em;
  right: 0.3em;
  position: absolute;
}

</style>
