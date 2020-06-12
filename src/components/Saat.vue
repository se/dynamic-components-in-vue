<template>
  <div>
    {{ prefix }}{{ saat }}

    <button @click="click">Güncel Saat</button>
  </div>
</template>

<script>
export default {
  props: {
    saat: {
      type: String,
    },
    prefix: {
      type: String,
    },
  },
  methods: {
    click() {
      this.$emit("click", new Date());
      this.$emit("update", "GUNCELLEME");
    },
  },
};
</script>

<style lang="scss" scoped></style>
