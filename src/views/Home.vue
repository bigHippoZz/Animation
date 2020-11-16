<template>
  <div class="home">
    <div @click="handleClick">bilibili导航栏</div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { useRouter } from "vue-router";
export default defineComponent({
  name: "Home",
  setup() {
    const router = useRouter();
    function handleClick() {
      router.push({ path: "/bilibiliNavigationBar" });
    }
    return {
      handleClick,
    };
  },
});
</script>
