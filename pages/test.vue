<template lang='pug'>
v-form(netflify @submit.prevent='submit')
     input(type='hidden' name='form-name' value='test un')
     v-text-field(name='message' v-model='form.message' label='message')
     v-btn(type='submit') submit
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