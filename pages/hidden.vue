<template lang='pug'>
div
     form(name='hidden' netflify hidden)#form
          input(name='form-name' value='hidden')
          input(name='message' v-model='form.message')
     v-form
          v-text-field(v-model='form.message' label='message')
          v-btn(type='submit' form='form') submit
</template>

<script lang='coffee'>
export default
     data: ->
          form:
               'form-name': 'test un'
               message: ''
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