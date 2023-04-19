<template>
  <div class="container">
    <base-header label="Dashboard" />

    <div>
      <card
        :title="title"
        :title-classes="titleClasses"
        :action="'Ver mais'"
        class="w-1/4"
        @click="openMovie()"
      >
        <div class="space-y-2">
          <p class="font-semibold text-base text-gray-700">Atores:</p>
          <span class="text-gray-400 text-sm">
            Leonardo DiCaprio, Kate Winslet
          </span>

          <p class="font-semibold text-base text-gray-700">Gênero:</p>
          <span class="text-gray-400 text-sm"> Drama, Romance</span>

          <p class="font-semibold text-base text-gray-700">Duração:</p>
          <span class="text-gray-400 text-sm"> 3h 15min</span>

          <p class="font-semibold text-base text-gray-700">Ano:</p>
          <span class="text-gray-400 text-sm"> 1997</span>
        </div>
      </card>
    </div>
  </div>
</template>

<script>
import BaseHeader from '~/components/Header/BaseHeader.vue'
import Card from '~/components/Cards/Card.vue'

export default {
  components: {
    BaseHeader,
    Card,
  },

  data() {
    return {
      title: 'Titanic',
      titleClasses: 'text-lg font-bold text-gray-700',
    }
  },

  methods: {
    openMovie() {
      console.log('Clicou no botão')
    },
  },
}
</script>

<style>
.el-card {
  background: #fff;
  border-radius: 20px;
}
</style>
