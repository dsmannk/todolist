<template>
    <div>
        <v-card class="pa-2 ma-2 rounded-lg"
                :class="{'done': list.status === 'done'}"
                v-for="(list, index) in todoList" :key="index">
            <p>{{ list.memo }}</p>
            <v-btn
                v-if="list.status === 'created'"
                class="mobile ma-1"
                @click="$emit('statusControl', index, 'done')"
                fab icon small outlined color="green"
                ><font-awesome-icon :icon="['fas', 'check']"/></v-btn>

            <v-btn
                v-else
                class="mobile ma-1"
                @click="$emit('statusControl', index, 'created')"
                fab icon small outlined color="blue"
                ><font-awesome-icon :icon="['fas', 'redo-alt']"/></v-btn>
            <v-btn
                class="mobile ma-1"
                fab icon outlined small color="red"
                @click="$emit('listDelete', index)"
                ><font-awesome-icon :icon="['fas', 'trash-alt']"/></v-btn>
          <v-btn
              v-if="list.status === 'created'"
              class="mobile ma-1"
              fab icon outlined small color="yellow"
              @click="listEdit(list.memo, index)"
          ><font-awesome-icon :icon="['fas', 'edit']"/></v-btn>
        </v-card>
    </div>
</template>

<script>
import { eventBus } from "../main"
export default {
    props: ["todoList"],
    methods: {
        listEdit(memo, index) {
          eventBus.listEdit(memo, index)
        }
    }
};
</script>

<style scoped>
.done {
  background-color: rgba(0, 0, 0, 0.1);
}
.done p {
  text-decoration: line-through;
  color: rgba(0, 0, 0, 0.5);
}
</style>
