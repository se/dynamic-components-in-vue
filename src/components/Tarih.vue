<template>
  <div>
    Tarih: {{ tarih }}
  </div>
</template>

<script>
export default {
  props: {
    tarih: {
      type: String,
    },
  },
};
</script>

<style lang="scss" scoped></style>
