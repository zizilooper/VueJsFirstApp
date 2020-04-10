<template>
  <v-app>
    <v-container>
      <v-row>
        <v-col cols="12">
          <v-progress-linear v-model="counter"></v-progress-linear>
        </v-col>
      </v-row>
      <v-row justify="center">
        <v-col cols="4">
          <v-text-field v-model="data"></v-text-field>
          <v-btn id="btn" @click="addData" @submit.prevent dark large
            >Click</v-btn
          >
        </v-col>
      </v-row>
      <v-row class="cards">
      <div v-for="(item, index) in items" :key="index" >
        <div @click="deleteItem(index)">
          <v-card class="card">
            <v-card-text>
              <h4>{{ item }}</h4>
            </v-card-text>
          </v-card>
        </div>
      </div>
      </v-row>
    </v-container>
  </v-app>
</template>

<script>
export default {
  name: "App",

  data: () => ({
    data: "",
    items: [],
    dele: "",
    counter: "0",
  }),
  methods: {
    addData() {
      if (this.data !== "") {
        this.items.push(this.data);
        console.log(this.items);
        this.data = "";
        this.counter += 1;
      }
    },
    deleteItem(index) {
      this.items.splice(index, 1);
      console.log(`delete`);
      this.counter -= 1;
    },
  },
};
</script>

<style scoped>
.card {
  width: 200px;
  height: 50px;
  float: left;
  margin: 10px;


}
.cards {
  width: 100%;
  background-color: rgb(230, 233, 238);
  display: inline-block;
  border-radius: 6px;
  color: black;
}
#btn{
  background-color: rgb(78, 96, 128);
}

</style>
