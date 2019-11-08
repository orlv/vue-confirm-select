<template id="vue-confirm-select-template">
    <span class="confirm-select">
        <span v-if="!busy">
            <span>{{ selectedTitle }}</span>
            <span class="text-button text-button-green p-0" @click="busy = true">{{ this.edit || 'Edit' }}</span>
        </span>
        <span v-else>
            <select v-model="selectedValue" @keydown.enter="confirm">
                <option v-for="el in list" :value="el.value">{{ el.title }}</option>
            </select>
            <span class="text-button text-button-red p-0" @click="confirm">{{ this.ok || 'OK' }}</span>
            <span class="text-button text-button-green p-0" @click="cancelClick">{{ this.cancel || 'Cancel' }}</span>
        </span>
    </span>
</template>

<script>
  import 'rlv-styles/styles.css'

  export default {
    template: '#vue-confirm-select-template',

    data () {
      return {
        busy: false,
        selectedValue: '',
        selectedTitle: ''
      }
    },

    props: ['callback', 'value', 'title', 'list', 'edit', 'ok', 'cancel'],

    created () {
      this.selectedValue = this.value || ''
      this.selectedTitle = this.title || ''
    },

    computed: {},

    methods: {
      confirm () {
        this.selectedTitle = this.list.filter(el => el.value === this.selectedValue)[0].title
        this.callback(this.selectedValue)
        this.busy = false
      },

      cancelClick () {
        this.selectedValue = this.value || ''
        this.selectedTitle = this.title || ''
        this.busy = false
      }
    }
  }
</script>

<style scoped>
    .confirm-select select {
        outline: none;
        font-size: 1em;
        -webkit-appearance: none;
        border: 1px solid #dedede;
        height: 1.45em;
        text-align-last: center;
        background-color: #ffffff;
    }
</style>
