<template>
  <div class="search">

    <div class="header">
      <h1>Поиск слов</h1>
    </div>

    <input 
      type="text"
      @input="search_word = $event.target.value"
      placeholder="Word"
    />

    <div class="words-info">
      <p>
        Всего слов: {{ words.length }}
        <label class="divider">|</label> 
        Совпадений: {{ searching_words.length }}
      </p>
    </div>

    <hr>

    <div class="word-list">
      <p
        v-for="(word, i) in searching_words"
        :key="i"
      >
        {{ word }} <br>
      </p>
    </div>

  </div>
</template>

<script>

export default {
  name: 'SearchWords',

  props: {
    words: Array
  },

  data() {
    return {
      search_word: ''
    }
  },

  computed: {
    searching_words() {
      return this.words.filter(
        word => word.toLowerCase().includes(this.search_word.toLowerCase())
      );
    },

    name_matches() {
      return this.search_word == '' 
                    ? 0
                    : this.searching_words.length;
    }

  }
  
}

</script>

<style>

input {
  background-color: #333;
  color: aliceblue;
}

.search {
  margin-top: 3em;
}

.header {
  margin-bottom: 2em;
}

.words-info {
  margin-top: 0.2em;
  margin-bottom: 2em;
  margin-left: 0.7em;
}

.divider {
  margin-left: 1.5em;
  margin-right: 1.5em;
}

.word-list {
  margin-top: 2em;
}

</style>