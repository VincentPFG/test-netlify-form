<template lang='pug'>
div
     //- form(name='hidden' netlify hidden)#form
     //-      input(name='form-name' value='hidden')
     //-      input(name='message' v-model='form.message')
     //- v-form
     //-      v-text-field(v-model='form.message' label='message')
     //-      v-btn(type='submit' form='form') submit

     //- v-form(name='hidden' netlify)
     //-      div(hidden)
     //-           input(name='form-name' value='hidden')
     //-           input(name='message' v-model='form.message')
     //-           input(name='name' v-model='form.name')
     //-           input(name='email' v-model='form.email')
     //-      v-container
     //-           v-layout(wrap)
     //-                v-flex(xs12 lg6)
     //-                     v-text-field(v-model='form.name' label='name')
     //-                v-flex(xs12 lg6)
     //-                     v-text-field(v-model='form.email' label='email')
     //-           v-textarea(v-model='form.message' label='message')
     //-           v-layout(justify-center)
     //-                v-btn(type='submit').center submit

     v-dialog(v-model='dialog')
          template(v-slot:activator='{on}')
               v-layout(justify-center)
                    v-btn(v-on='on') laisser un message
          v-form(netlify name='hidden')
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
                         v-btn(type='submit') submit
</template>

<script lang='coffee'>
export default
     data: ->
          form:
               message: ''
               name: ''
               email: ''
               civil: ''
          dialog: off
          civil: ['Madame', 'Monsieur']
     methods:
          encode: (data) -> ("#{encodeURIComponent key}=#{encodeURIComponent data[key]}" for key of data).join '&'
          submit: ->
               fetch '/',
                    method: 'POST'
                    headers: 'Content-Type': 'application/x-www-form-urlencoded'
                    body: @encode @form
               .then -> alert 'success'
               .error -> alert 'failure'
</script>