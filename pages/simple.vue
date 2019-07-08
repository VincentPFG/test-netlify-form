<template lang='pug'>
v-form(netlify name='simple')
     div(hidden)
          input(name='form-name' value='simple')
          input(name='civil' v-model='civil')
          input(name='name' v-model='name')
          input(name='email' v-model='email')
          textarea(name='message' v-model='message')
     v-select(:items='choix' label='civil' v-model='civil')
     v-text-field(label='name' v-model='name')
     v-text-field(label='email' v-model='email')
     v-textarea(label='message' v-model='message')

     v-btn(type='submit') submit
</template>

<script lang='coffee'>
export default
     data: ->
          civil: ''
          name: ''
          email: ''
          message: ''

          choix: ['madame', 'monsieur']
</script>