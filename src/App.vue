<template>
  <div class="main-container">
    <v-container>
      <v-card class="pa-4 mb-2">
        <v-row>
          <v-col cols="12">
            <h1>Hello World! - Splitter Here!</h1>
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="12">
            <v-textarea variant="outlined" label="Input Raw" hide-details v-model="inputRaw"></v-textarea>
            <label class="text-caption">Raw length: {{ inputRaw.length }}</label>
          </v-col>
        </v-row>
      </v-card>
      <v-row>
        <v-col cols="6">
          <mode-one :data="data" :inputRaw="inputRaw"></mode-one>
        </v-col>
        <v-col cols="6">
          <mode-two :data="data" :inputRaw="inputRaw"></mode-two>
        </v-col>
      </v-row>
    </v-container>
    <v-footer class="text-center d-flex flex-column">
      <v-divider></v-divider>
      <div>
        {{ new Date().getFullYear() }} — made with ❤️ by FarhanNH
      </div>
    </v-footer>
  </div>
</template>
<script>
import ModeOne from './components/ModeOne.vue';
import ModeTwo from './components/ModeTwo.vue';

export default {
  components: {
    ModeOne,
    ModeTwo
  },
  data() {
    return {
      inputRaw: "",
      mode: "mode1",
      modeList: ["mode1", "mode2", "mode3"],
      start: 0,
      end: 0,
      result: "",
      data: ""
    };
  },
};
</script>