<template lang='pug'>
v-dialog(v-model='dialog')
     template(v-slot:activator='{on}')
          v-layout(justify-center)
               v-btn(v-on='on') laisser un message
     v-form(name='contact' netlify)
          div(hidden)
               input(name='form-name' value='hidden')
               input(name='message' v-model='form.message')
               input(name='name' v-model='form.name')
               input(name='email' v-model='form.email')
          v-container
               v-layout(wrap)
                    v-flex(xs12 md2)
                         v-select(:items='civil' label='civilité' v-model='form.civil')
                    v-flex(xs12 md5)
                         v-text-field(v-model='form.name' label='name')
                    v-flex(xs12 md5)
                         v-text-field(v-model='form.email' label='email')

               v-textarea(v-model='form.message' label='message')
               v-layout(justify-center)
                    v-btn(type='submit') envoyer
</template>

<script lang='coffee'>
export default
     data: ->
          form:
               message: ''
               name: ''
               email: ''
               civil: ''
</script>