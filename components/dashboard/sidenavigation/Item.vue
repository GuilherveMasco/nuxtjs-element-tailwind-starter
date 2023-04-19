<template>
  <li>
    <router-link :to="to">
      <span
        class="duration-200 flex font-thin items-center justify-start my-2 p-4 transition-colors text-gray-400 uppercase w-full lg:hover:text-yellow-300"
        :class="
          $route.path === to &&
          'bg-gradient-to-r border-r-4 border-yellow-300 border-r-4 border-yellow-300 from-white to-yellow-100 text-yellow-300'
        "
      >
        <span>
          <slot />
        </span>
        <span class="font-normal mx-4 text-sm">
          {{ title }}
        </span>
      </span>
    </router-link>
  </li>
</template>

<script>
export default {
  name: 'SidenavItem',
  props: {
    to: {
      type: String,
      default: '',
    },
    title: {
      type: String,
      default: '',
    },
  },
}
</script>
