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
        <label v-if="inputRaw.length > 0" class="text-caption">Raw length: {{ inputRaw.length }}</label>
      </v-col>
    </v-row>
    <mode-one v-if="mode == 'mode1'" :data="data" :inputRaw="inputRaw"></mode-one>
    <mode-two v-if="mode == 'mode2'" :data="data" :inputRaw="inputRaw"></mode-two>
  </v-container>
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
      mode: "mode2",
      modeList: ["mode1", "mode2", "mode3"],
      start: 0,
      end: 0,
      result: "",
      data: ""
    };
  },
};
</script>