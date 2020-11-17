<template>
  <div class="animated-banner" @mousemove="handleMousemove">
    <div
      class="layer"
      v-for="item in images"
      :key="item._id"
      :style="{
        filter: `blur(${item.blur}px)`,
        transform: `translateX(${item.offset}px)`,
      }"
    >
      <img :src="item.path" />
    </div>
  </div>
</template>

<script lang="ts">
import { onMounted, computed, reactive, ref, readonly, toRefs } from "vue";
const IMAGES_LIST = [
  require("./assets/8e084d67aa18ed9c42dce043e06e16b79cbb50ef.png"),
  require("./assets/082e39ef757826401ef82da818310d42e05bc2de.png"),
  require("./assets/dbd5c17c4315714de9e4ee119694d2e9efaf9639.png"),
  require("./assets/cd9be0a2716adbae85fd899259381c4b2c2893c7.png"),
  require("./assets/88537437a7916ecde847fa46652b44fbd3cbbb06.png"),
  require("./assets/37d9a93baa55870506a6f3e6308e7a0c386b97c7.png"),
];
export default {
  name: "bilibiliNavigationBar",
  setup() {
    onMounted(() => {
      console.groupCollapsed("win width");
      console.log(window.innerWidth, "window.innerWidth");
      console.log(window.outerWidth, "window.outerWidth");
      console.log(process.env);
      console.groupEnd();
    });
    const imagesPathSlice = (path: string): string => path.split("/")[2];
    const images = reactive(
      IMAGES_LIST.map((image) => ({
        path: image,
        _id: imagesPathSlice(image),
        blur: ref(2),
        offset: ref(10),
      }))
    );
    const handleMousemove = (e: MouseEvent) => {
      const percentage = e.clientX / window.innerWidth;
      const offset = percentage * 10;
      const blur = 20;
      images.forEach((image, index) => {
        image.offset = offset * 1.3;
        image.blur = Math.pow(index / images.length - percentage, 2) * blur;
      });
    };
    return { handleMousemove, images };
  },
};
</script>

<style lang="less" scoped>
.animated-banner {
  position: relative;
  height: 160px;
  width: 100%;
  overflow: hidden;
  .layer {
    position: absolute;
    top: 0;
    left: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;
    width: 100%;
    img {
      display: block;
      width: 110%;
      height: 100%;
      object-fit: cover;
    }
  }
}
</style>
