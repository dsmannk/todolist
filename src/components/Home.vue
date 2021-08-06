<template>
  <v-container fluid grid-list-sm pa-0>
    <v-layout row wrap>
      <v-flex xs6>
        <List :todoList="todoList"></List>
      </v-flex>
    </v-layout>
    <v-layout row wrap>
      <v-flex xs6>
        <ListAdd @listAdd="listAdd"></ListAdd>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
import List from "./List";
import ListAdd from "./ListAdd";

export default {
  components: {
    List,
    ListAdd,
  },
  data: () => ({
    todoList: [],
  }),
  methods: {
    listAdd(memo) {
      console.log("받았어");
      this.todoList.push({ memo: memo, status: "created" });
    },
  },
};
</script>
