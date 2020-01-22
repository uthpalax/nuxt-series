<template>
  <div class="container">
    <div>
      <h1 class="text-4xl font-semibold text-gray-800 mb-8">
        DoingITeasyChannel - Nuxt Series
      </h1>
      <nuxt-link
        to="create"
        class="m-2 bg-purple-700 rounded p-2 text-white font-semibold"
      >
        Create Character
      </nuxt-link>
      <div class="flex">
        <ul class="w-64 px-2 text-gray-600">
          <li v-for="character in characters" :key="character.id">
            <nuxt-link
              :to="character.id"
              class="hover:font-bold hover:text-gray-900 leading-loose"
            >
              {{ character.name }}
            </nuxt-link>
          </li>
        </ul>
        <div class="flex-grow bg-white min-h-full">
          <nuxt-child :key="$route.params.id"></nuxt-child>
        </div>
      </div>
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
  fetch({ redirect }) {
    redirect('/1')
  },
  apollo: {
    characters: gql`
      query getCharacters {
        characters {
          id
          name
        }
      }
    `
  }
}
</script>
