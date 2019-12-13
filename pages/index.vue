<template>
  <div class="container">
    <div>
      <h1 class="text-4xl font-semibold text-gray-800">
        DoingITeasyChannel - Nuxt Series
      </h1>
      <ul>
        <li v-for="character in characters.results" :key="character.id">
          {{ character.name }} -
          {{ character.status }}
        </li>
      </ul>
    </div>
  </div>
</template>
<script>
import gql from 'graphql-tag'
export default {
  apollo: {
    characters: gql`
      query getCharacters {
        characters {
          results {
            id
            name
            status
          }
        }
      }
    `
  }
}
</script>
