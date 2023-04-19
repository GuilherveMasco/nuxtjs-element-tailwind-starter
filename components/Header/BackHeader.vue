<template>
  <div style="margin-bottom: 1rem">
    <el-page-header @back="goBack" :content="label"> </el-page-header>
    <br />

    <span>
      <el-breadcrumb separator-class="el-icon-arrow-right">
        <el-breadcrumb-item v-for="item in itens" :key="item">
          {{ item }}
        </el-breadcrumb-item>
      </el-breadcrumb>
    </span>
  </div>
</template>

<script>
export default {
  props: ["label", "itens", "goBackRoute"],
  methods: {
    goBack() {
      this.$nuxt.$options.router.push(this.goBackRoute);
    },
  },
};
</script>

<style>
</style>