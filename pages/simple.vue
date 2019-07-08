<template lang='pug'>
v-form(netlify name='simple')
     div(hidden)
          input(name='name' v-model='name')
          input(name='email' v-model='email')
          input(name='message' v-model='message')
     v-text-field(label='name' v-model='name')
     v-text-field(label='email' v-model='email')
     v-textarea(label='message' v-model='message')

     v-btn(type='submit') submit
</template>

<script lang='coffee'>
export default
     data: ->
          name: ''
          email: ''
          message: ''
</script>