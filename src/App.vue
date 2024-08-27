<template>
  <v-container>
    <v-row>
      <v-col cols="12">
        <h1>Hello World!</h1>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12">
        <v-textarea variant="outlined" label="Input Raw" hide-details v-model="inputRaw"></v-textarea>
        <label v-if="inputRaw.length > 0">{{ inputRaw.length }}</label>
      </v-col>
    </v-row>
    <mode-one :data="data" :inputRaw="inputRaw"></mode-one>
  </v-container>
</template>
<script>
import ModeOne from './components/ModeOne.vue';

export default {
  components: {
    ModeOne
  },
  data() {
    return {
      inputRaw: "",
      mode: ["mode1", "mode2", "mode3"],
      start: 0,
      end: 0,
      result: "",
      data: ""
    };
  },
};
</script>