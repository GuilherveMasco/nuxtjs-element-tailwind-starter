<template>
  <div>
    <el-card>
      <div slot="header" class="clearfix">
        <span :class="titleClasses"> {{ title }} </span>
        <el-button style="float: right" type="text" @click="callToAction()">
          {{ action }}
        </el-button>
      </div>
      <div class="flex items-center">
        <el-image
          :src="imageUrl"
          :fit="imageFit"
          class="w-2/3 h-2/3 mx-auto"
        ></el-image>
        <slot></slot>
      </div>
      <div slot="footer">{{ footer }}</div>
    </el-card>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    title: {
      type: String,
      default: 'Título do card',
    },
    action: {
      type: String,
      default: 'Função do botão',
    },
    footer: {
      type: String,
      default: 'Rodapé do card',
    },
    titleClasses: {
      type: String,
      default: 'text-lg font-bold text-gray-800',
    },
    imageUrl: {
      type: String,
      default:
        'https://uauposters.com.br/media/catalog/product/cache/1/thumbnail/800x930/9df78eab33525d08d6e5fb8d27136e95/1/9/198920140605-198920140605-uau-posters-filmes-titanic--titanic-2.jpg',
    },
    imageFit: {
      type: String,
      default: 'cover',
    },
  },

  methods: {
    callToAction() {
      this.$emit('click')
    },
  },
}
</script>

