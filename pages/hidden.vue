<template lang='pug'>
div
     //- form(name='hidden' netlify hidden)#form
     //-      input(name='form-name' value='hidden')
     //-      input(name='message' v-model='form.message')
     //- v-form
     //-      v-text-field(v-model='form.message' label='message')
     //-      v-btn(type='submit' form='form') submit

     v-form(name='hidden' netlify)
          div(hidden)
               input(name='form-name' value='hidden')
               input(name='message' v-model='form.message')
               input(name='name' v-model='form.name')

          v-text-field(v-model='form.name' label='name')
          v-text-field(v-model='form.message' label='message')

          v-btn(type='submit') submit
</template>

<script lang='coffee'>
export default
     data: ->
          form:
               'form-name': 'test un'
               message: ''
               name: ''
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