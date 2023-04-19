<template>
  <div class="my-4 lg:my-8">
    <span class="text-[#FECC00] text-3xl font-semibold">
      {{ label }}
    </span>

    <span>
      <el-breadcrumb separator-class="el-icon-arrow-right">
        <el-breadcrumb-item v-for="(item, index) in itens" :key="item">
          <nuxt-link v-if="index == 0" :to="url">
            <span
              class="text-sm text-yellow-300 lg:text-lg"
              style="color: #fecc00"
            >
              {{ item }}
            </span>
          </nuxt-link>
          <span v-else class="text-sm text-yellow-300 lg:text-lg">
            {{ item }}
          </span>
        </el-breadcrumb-item>
      </el-breadcrumb>
    </span>
  </div>
</template>

<script>
export default {
  props: {
    label: {
      type: String,
      description: 'Título da página',
      default: '',
      required: false,
    },
    url: {
      type: String,
      description: 'Link para navegação',
      default: '',
      required: false,
    },
    itens: {
      type: Array,
      description: 'Caminho',
      default() {
        return []
      },
    },
  },
}
</script>

<style>
</style>
