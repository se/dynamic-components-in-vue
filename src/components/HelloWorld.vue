<template>
  <div>
    <template v-for="c in dynamicComponents">
      <component
        :is="c.component"
        :key="c.key"
        v-bind="c.data"
        v-on="c.events"
      />
    </template>
    <button @click="() => (this.selectedUser = 'Mahmut')">İsmi Güncelle</button>
  </div>
</template>

<script>
import Yazi from "./Yazi";
import Saat from "./Saat";
import Tarih from "./Tarih";
export default {
  name: "HelloWorld",
  components: {
    Yazi,
    Saat,
    Tarih,
  },
  props: {
    msg: String,
  },
  data() {
    return {
      selectedUser: "Selçuk",
      dynamicComponents: [
        {
          name: "YAZI",
          component: Yazi,
          data: {
            prefix: "Selamlar, ",
            text: () => this.selectedUser,
            suffix: ". Nasılsın?",
            type: "UPPER",
          },
          events: null,
        },
        {
          name: "SAAT",
          component: Saat,
          data: {
            saat: "13:21",
            prefix: "SAAT:",
          },
          events: {
            click: (data) => {
              console.log("tıklama durumunu yakaladım!", data);
            },
            update: (data) => {
              console.log("update oldu", data);
            },
          },
        },
        {
          name: "TARIH",
          component: Tarih,
          data: {
            tarih: "30.06.1987",
          },
          events: null,
        },
      ],
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
