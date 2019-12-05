<template>
  <div>
    <ul>
      <li>
        <nuxt-link to="/nav/about">About</nuxt-link>
        <nuxt-link to="/nav/contact">Contact</nuxt-link>
      </li>
    </ul>
    <div class="bg-gray-500">
      <nuxt-child />
    </div>
  </div>
</template>
