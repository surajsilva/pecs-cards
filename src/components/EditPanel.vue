<template>
    <v-slide-y-transition>
      <div v-show="showPanel" class="slide-panel">
        <div class="panel-content">
          <div class="input-fields">
            <v-text-field v-model="height" label="Height"></v-text-field>
            <v-text-field v-model="width" label="Width"></v-text-field>
            <v-text-field v-model="caption" label="Caption"></v-text-field>
            <v-text-field v-model="imagePath" label="Image Path"></v-text-field>
            <v-slider
                v-model="rotation"
                label="Rotation" 
                :ticks="ticks"
                :max="4"
                step="1"
                show-ticks="always"
                tick-size="4"
            ></v-slider>

          </div>
          <div class="button-container">
            <v-btn text color="primary" @click="cancel">Cancel</v-btn>
            <div style="width: 10px;"></div>
            <v-btn text color="primary" @click="save">Save</v-btn>
          </div>
        </div>
      </div>
    </v-slide-y-transition>
  </template>
  
  <script>
  export default {
    name: 'EditPanel',
    data() {
      return {
        ticks: {
            0: 0,
            1: 90,
            2: 180,
            3: 270,
            4: 360
        },
        showPanel: false,
        height: '',
        width: '',
        caption: '',
        imagePath: '',
        rotation: 0
      }
    },
    methods: {
      save() {
        // Save logic
        this.showPanel = false;
        this.$emit('close');
      },
      cancel() {
        // Cancel logic
        this.showPanel = false;
        this.$emit('close');
      }
    }
  }
  </script>
  
  <style>
  .slide-panel {
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: auto;
    width: 600px;
    background-color: #F5F5F5;
    z-index: 9999;
    display: flex;
    justify-content: flex-end;
    align-items: flex-start;
  }
  
  .panel-content {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: 100%;
    width: 100%;
    padding: 16px;
    box-sizing: border-box;
  }
  
  .input-fields {
    flex: 1;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: stretch;
  }
  
  .button-container {
    display: flex;
    flex-direction: row;
    justify-content: flex-end;
    align-items: center;
    margin-top: 10px;
  }
  </style>
  