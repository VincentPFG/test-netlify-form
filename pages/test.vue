<template lang='pug'>
v-form(netflify @submit.prevent='submit')
     v-text-field(v-model='form.message' label='message')
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
          # submit: ->
          #      @$axios.post '/', @encode @form
          #           .then ->
          #                alert 'success'
          #           .catch ->
          #                alert 'failure'
          #           .then ->
          #                alert 'called'
</script>