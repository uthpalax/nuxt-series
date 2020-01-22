<template>
  <div>
    <h2 class="mb-4">Create Character</h2>
    <form action="" @submit.prevent="createCharacter">
      <div class="mb-4">
        <input
          v-model="name"
          type="text"
          class="shadow border rounded py-2 px-3 text-gray-700 leading-tight"
          placeholder="name"
        />
      </div>
      <div class="mb-4">
        <input
          v-model="gender"
          type="text"
          class="shadow border rounded py-2 px-3 text-gray-700 leading-tight"
          placeholder="gender"
        />
      </div>
      <div class="mb-4">
        <input
          v-model="status"
          type="text"
          class="shadow border rounded py-2 px-3 text-gray-700 leading-tight"
          placeholder="status"
        />
      </div>
      <div class="mb-4">
        <input
          v-model="image"
          type="text"
          class="shadow border rounded py-2 px-3 text-gray-700 leading-tight"
          placeholder="image"
        />
      </div>
      <button
        class="bg-green-600 py-2 px-3 font-semibold text-white"
        type="submit"
      >
        Create Character
      </button>
    </form>
  </div>
</template>

<script>
import gql from 'graphql-tag'

export default {
  name: 'CreateCharacter',
  data() {
    return {
      name: '',
      status: '',
      gender: '',
      image: ''
    }
  },
  methods: {
    createCharacter(event) {
      this.$apollo
        .mutate({
          mutation: gql`
            mutation(
              $name: String
              $status: String
              $gender: String
              $image: String
            ) {
              addCharacter(
                name: $name
                status: $status
                gender: $gender
                image: $image
              ) {
                name
                gender
              }
            }
          `,
          variables: {
            name: this.name,
            status: this.status,
            gender: this.gender,
            image: this.image
          }
        })
        .then((data) => {
          event.target.reset()
        })
    }
  }
}
</script>

<style></style>
