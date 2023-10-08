<template>
  <div class="container my-container">
    <div class="row">
      <button 
        type="btn" 
        class="add-word-btn btn btn-success"
        @click="add_new_word()"
      >
        Add word
      </button>
  
      <button 
        type="btn" 
        class="remove-word-btn btn btn-danger"
        @click="pop_word()"
      >
        Remove word
      </button>
    </div>

    <hr class="hr-divider">
  
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
      
      if (!new_word) 
        return;

      let have_word;
      this.words.forEach(word => {
        if (word.toLowerCase() === new_word.toLowerCase()) {
          have_word = true;
          return;
        }
      });

      if (have_word)
        return;

      this.words.push(new_word);
    
    },

    pop_word() {
      const delete_word = prompt("Введите удаляемое слово: ");

      if (!delete_word)
        return;
      
      this.words = this.words.filter(el => el.toLowerCase() !== delete_word.toLowerCase());

    }
  }
}

</script>


<style>

body {
  background-color: #333;
  color: aliceblue;
}

.my-container {
  position: relative;
  max-width: 30em;
}

.add-word-btn {
  width: 8em;
  top: 0;
  right: 0;
  position: absolute;
  margin-top: 0.3em;
  margin-right: 0.3em;
}

.remove-word-btn {
  width: 8em;
  top: 0;
  left: 0;
  position: absolute;
  margin-top: 0.3em;
  margin-left: 0.3em;
}

.hr-divider {
  margin-top: 3.05em;
}

</style>
