<template>
  <!-- 使用手册 -->
  <!--   <loadblockVue
       :bheight="10"
       :bwith="1000"
       :swith="200"
       color="aqua"
       other="#fff"
       @loadOk="loadOkFn"
       >1231321</loadblockVue
     > -->

  <div class="main">
    <div class="mask"><slot>♥</slot></div>
    <div
      class="outBox"
      :style="{
        width: `${bwith}px`,
        backgroundColor: `${other}`,
        height: `${bheight}px`,
      }"
    >
      <div
        class="inBox"
        :style="{ width: `${swith}px`, backgroundColor: `${color}` }"
      ></div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  props: {
    bwith: {
      type: Number,
    },
    swith: {
      type: Number,
    },
    color: {
      type: String,
    },
    other: {
      type: String,
    },
    bheight: {
      type: Number,
    },
  },
  created() {},
  watch: {
    swith: {
      immediate: true,
      handler() {
        if (this.swith !== this.bwith) return;
        this.$emit("loadOk");
      },
    },
  },
  methods: {},
};
</script>

<style scoped lang="less">
.main {
  position: relative;
  .mask {
    position: absolute;
    top: 0;
    left: 0;
  }
}

.outBox {
  width: 200px;
  height: 30px;
  background-color: #fff;
  border: 1px solid black;
  transition: all 0.3s;
  .inBox {
    height: 100%;
    width: 100px;
    background-color: #eee;
    transition: all 0.3s;
  }
}
</style>
