<template>
  <div class="mode-one">
    <v-row>
      <v-col cols="12">
        <h2>The character you want to take</h2>
      </v-col>
    </v-row>
    <v-row class="text-center align-center">
      <v-col cols="5">
        <v-text-field variant="outlined" label="Start" hide-details type="number" v-model="start"></v-text-field>
      </v-col>
      <v-col cols="2">
        <label>to</label>
      </v-col>
      <v-col cols="5">
        <v-text-field variant="outlined" label="End" hide-details type="number" v-model="end"></v-text-field>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12">
        <v-textarea variant="outlined" label="Result" readonly hide-details v-model="result"></v-textarea>
        <label v-if="result.length > 0">{{ result.length }}</label>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  name: "ModeOne",
  props: ["data", "inputRaw"],
  data() {
    return {
      start: 0,
      end: 0,
      result: ""
    };
  },
  watch: {
    start: function(newVal) {
      this.result = this.inputRaw.slice(newVal, this.end);
    },
    end: function(newVal) {
      console.log(this.inputRaw)
      this.result = this.inputRaw.slice(this.start, newVal);
    },
    inputRaw: function() {
      this.result = this.inputRaw.slice(this.start, this.end);
    }
  }
}
</script>

<style>

</style>