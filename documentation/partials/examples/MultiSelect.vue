<template lang="pug">
div
  label.typo__label Simple select / dropdown
  multiselect(
    v-model="value",
    :options="options",
    :multiple="true",
    :close-on-select="false",
    :clear-on-select="false",
    :hide-selected="true",
    :preserve-search="true",
    placeholder="Pick some"
    label="name",
    track-by="name",
    :is-open="isOpen",
    :preselect-first="true",
    @open="open",
    @close="close"
  )
    template(slot="tag", slot-scope="props")
      span.custom__tag
        span {{ props.option.language }}
        span.custom__remove(@click="props.remove(props.option)") ❌
  pre.language-json
    code.
      {{ value  }}

</template>

<script>
import Multiselect from 'vue-multiselect'

export default {
  components: {
    Multiselect
  },
  data () {
    return {
      value: [],
      isOpen: false,
      options: [
        { name: 'Vue.js', language: 'JavaScript' },
        { name: 'Adonis', language: 'JavaScript' },
        { name: 'Rails', language: 'Ruby' },
        { name: 'Sinatra', language: 'Ruby' },
        { name: 'Laravel', language: 'PHP' },
        { name: 'Phoenix', language: 'Elixir' }
      ]
    }
  },
  methods: {
    open() {
      this.isOpen = true
    },
    close() {
      this.isOpen = false
    }
  }
}
</script>

<style lang="sass">
.custom__tag
  display: inline-block
  padding: 3px 12px
  background: #d2d7ff
  margin-right: 8px
  margin-bottom: 8px
  border-radius: 10px
  cursor: pointer

  &:nth-child(even)
    background: #daffee

  &:hover
    background: #eaeaea

.custom__remove
  padding: 0px
  font-size: 10px
  margin-left: 5px
</style>
