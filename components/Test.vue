<!-- Please remove this file from your project -->
<template>
  <div>
    <h1>Create Repository</h1>
    <div>
      <div class="input-item">
        <p class="head">repository name</p>
        <input v-model="name" type="text" />
      </div>
      <div class="input-item">
        <p class="head">private</p>
        <div class="radio-wrapper">
          <div class="radio-item">
            <p>true</p>
            <input
              v-model="isPrivate"
              type="radio"
              name="private"
              value="true"
            />
          </div>
          <div class="radio-item">
            <p>false</p>
            <input
              v-model="isPrivate"
              type="radio"
              name="private"
              value="false"
            />
          </div>
        </div>
      </div>
      <div class="btn-wrapper">
        <button @click="submit">submit</button>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  data() {
    return {
      name: '',
      isPrivate: true,
    }
  },
  methods: {
    submit() {
      if (!this.name) return
      const params = {
        name: this.name,
        private: this.isPrivate,
      }

      this.$axios
        .$post('https://test-2d7c6.web.app/repository', params)
        .catch((err) => {
          return err.response
        })
    },
  },
})
</script>

<style scoped>
p {
  margin: 0;
}
.input-item {
  margin-bottom: 40px;
}
.head {
  font-weight: bold;
}
.radio-wrapper {
  display: flex;
}
.radio-item + .radio-item {
  margin-left: 20px;
}
.btn-wrapper {
  margin-top: 40px;
}
</style>
