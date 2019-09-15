<template>
  <div>
    <h1>Comments page with the slug parameter</h1>
    <p>{{ $route.params.slug }}</p>
  </div>
</template>

<script>
export default {
  validate({ params }) {
    // Must be a number
    return /^\d+$/.test(params.slug)
  }
}
</script>
