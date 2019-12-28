<template>
  <div
    v-if="!$apollo.queries.character.loading"
    class="rounded border m-2 flex"
  >
    <img :src="character.image" />
    <div class="p-2">
      <span>{{ character.status }}</span>
      <h1 class="text-2xl font-semibold">{{ character.name }}</h1>
      <h1>{{ character.gender }}</h1>
      <h1>{{ character.origin.name }}</h1>
    </div>
  </div>
</template>

<script>
import gql from 'graphql-tag'

export default {
  name: 'Character',
  apollo: {
    character: {
      query: gql`
        query getCharacter($id: ID) {
          character(id: $id) {
            id
            name
            status
            species
            gender
            image
            origin {
              name
            }
          }
        }
      `,
      variables() {
        return {
          id: this.$route.params.id
        }
      }
    }
  }
}
</script>
