<template>
  <div id="app">
    <h1>Books</h1>
    <ul>
      <li v-for="book in books" :key="book.id">
        {{ book.title }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      books: [],
    }
  },
  mounted() {
    // API-Abfrage an Django-Backend
    axios
      .get('http://localhost:8000/api/books/')
      .then(response => {
        this.books = response.data // Daten aus der API zuweisen
        console.log(response.data)
      })
      .catch(error => {
        console.error('Es gab einen Fehler beim Abrufen der Daten:', error)
      })
  },
}
</script>

<style>
/* Optional: CSS für Styling */
</style>
