<template>
  <div class="container">
    <div>
      <h1 class="text-4xl font-semibold text-gray-800 mb-8">
        DoingITeasyChannel - Nuxt Series
      </h1>
      <button
        class="bg-gray-700 p-4 border text-white"
        @click="characterId = characterId + 1"
      >
        Get next character
      </button>
      <h3 class="text-2xl">{{ character.id }} {{ character.name }}</h3>
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
  data() {
    return {
      characterId: 1
    }
  },
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
    `,
    character: {
      query: gql`
        query getCharacter($id: ID) {
          character(id: $id) {
            id
            name
          }
        }
      `,
      variables() {
        return {
          id: this.characterId
        }
      }
    }
  }
}
</script>
