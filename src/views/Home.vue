<template>
  <div class="home">
    <h2
      @click="handleClick(path)"
      v-for="{ name, path } in Animation"
      :key="path"
    >
      {{ name }}
    </h2>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { useRouter } from "vue-router";
export default defineComponent({
  name: "Home",
  setup() {
    const Animation = [
      {
        name: "bilibili导航栏",
        path: "/bilibiliNavigationBar",
      },

      {
        name: "文字渐变",
        path: "/textGradient",
      },
    ];
    const router = useRouter();
    function handleClick(path: string) {
      router.push({ path });
    }
    return {
      handleClick,
      Animation,
    };
  },
});
</script>
