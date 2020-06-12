<template>
  <div>Yazi: {{ prefix }}{{ textComputed }}{{ suffix }}</div>
</template>

<script>
export default {
  props: {
    text: {},
    prefix: {
      type: String,
    },
    suffix: {
      type: String,
    },
    type: {
      type: String,
    },
  },
  computed: {
    textComputed() {
      if (!this.text) {
        return "";
      }

      let returnText = "";

      if (typeof this.text === "function") {
        returnText = this.text();
      } else {
        returnText = this.text;
      }

      if (this.type === "UPPER") {
        return returnText.toUpperCase();
      }

      return returnText;
    },
  },
};
</script>

<style lang="scss" scoped></style>
