<template>
  <div class="kaiui-header">
    <span class="kaiui-h1 kaiui-header-text">{{ title }}</span>
  </div>
</template>

<script>
/**
 * The `<kaiui-header>` component.
 *
 * @author Sebastian Baar
 * @license MIT
 */
export default {
  name: "kaiui-header",
  props: {
    /**
     * The Title
     */
    title: {
      type: String,
      required: true,
    },
  },
  mounted() {
    this.$nextTick(() => {
      /**
       * @private
       */
      this.$root.$emit("update-header-registered", true);
    });
  },
  beforeDestroy() {
    /**
     * @private
     */
    this.$root.$emit("update-header-registered", false);
  },
};
</script>

<style scoped>
.kaiui-header {
  z-index: 1000;
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  min-height: 30px;
  height: 30px;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  white-space: nowrap;
  background-color: var(--header-background-color);
}

.kaiui-header-text {
  width: 100%;
  text-align: center;
  padding: 0 10px;
  text-overflow: ellipsis;
  overflow: hidden;
  color: var(--header-text-color);
}
</style>
