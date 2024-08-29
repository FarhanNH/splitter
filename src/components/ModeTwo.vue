<template>
  <v-card class="mode-two pa-4">
    <v-row>
      <v-col cols="12">
        <h3>Split sequence by length</h3>
      </v-col>
    </v-row>
    <v-row 
        v-for="(value, index) in chunks" 
        :key="index" 
        class="align-center">
        <v-col cols="2">
            {{ "Chunk " + (index + 1) }}
        </v-col>
        <v-col cols="3">
            <v-text-field 
                variant="outlined" 
                label="Length" 
                type="number" 
                hide-details 
                v-model="value.data">
            </v-text-field>
        </v-col>
        <v-col cols>
            <v-text-field 
                variant="outlined" 
                label="Chunk"
                hide-details 
                readonly
                v-model="value.chunk">
            </v-text-field>
        </v-col>
        <v-col cols="1">
            <v-btn 
                flat
                size="small"
                density="compact" 
                icon="mdi-minus" 
                color="warning" 
                @click="deleteChunk">
            </v-btn>
        </v-col>
    </v-row>
    <v-row>
        <v-col cols="1">
            <v-btn 
                flat
                size="small"
                density="compact" 
                icon="mdi-plus" 
                color="primary" 
                @click="addChunk">
            </v-btn>
        </v-col>
        <v-col cols="2">
            <v-btn 
                flat
                size="small"
                density="compact" 
                prepend-icon="$vuetify" 
                color="success" 
                :disabled="chunks <= 0 || inputRaw == ''" 
                :loading="isBusy"
                @click="spliceInputRaw">
                Split
            </v-btn>
        </v-col>
    </v-row>
  </v-card>
</template>

<script>
export default {
    name: "ModeTwo",
    props: ["data", "inputRaw"],
    data() {
        return {
            chunks: [],
            isBusy: false,
        };
    },
    methods: {
        addChunk() {
            this.chunks.push({ id: this.chunks.length + 1, data: 0, chunk: "" });
        },
        deleteChunk(index) {
            this.chunks.splice(index, 1);
        },
        spliceInputRaw() {
            this.isBusy = true;
            let newRaw = "";
            this.chunks.forEach((chunk, index) => {
                if (index == 0) {
                    newRaw = this.inputRaw.slice(newRaw.length, parseInt(chunk.data));
                } else {
                    newRaw = this.inputRaw.slice(newRaw.length, parseInt(chunk.data) + newRaw.length);
                }
                chunk.chunk = newRaw;
            });
            this.isBusy = false;
        }
    },
};
</script>