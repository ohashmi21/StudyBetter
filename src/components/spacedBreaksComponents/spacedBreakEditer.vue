<template>
    <div class="modal">
      <div>
        <h1>Time before break</h1>
        <p>Maximum:
          <input v-model="max" type="number">
          Minutes
        </p>
        <p>Minimum:
          <input v-model="min" type="number">
          Minutes
        </p>
        <p>Gap Length:
          <input v-model="length" type="number">
          Minutes
        </p>
        <button @click="saveChanges">Save Changes</button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'MyModal',
    data() {
      return {
        max: null,
        min: null,
        length: null,
      };
    },
    mounted() {
      // Load values from localStorage when the component is mounted
      this.max = localStorage.getItem('max') || null;
      this.min = localStorage.getItem('min') || null;
      this.length = localStorage.getItem('length') || null;
    },
    methods: {
    saveChanges() {
        // Validate the input values
        if (this.min < this.max) {
        // Save values to localStorage
        localStorage.setItem('max', this.max);
        localStorage.setItem('min', this.min);
        localStorage.setItem('length', this.length);
        console.log("Max: " + this.max + " Min: " + this.min);
        this.$emit('exit');
        } else {
        alert("Minimum must be less than the maximum!");
        }
    }
    }
  }
  </script>
  
  <style scoped>
  .modal {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 1000;
  }
  .modal p {
    color: white;
  }
  </style>
  