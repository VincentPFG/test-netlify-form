<template lang='pug'>
v-form(
     name='un-test'
     method='post'
     data-netlify='true'
     data-netlify-honeypot='bot-field'
)
     input(type='hidden' name='form-name' value='un-test')
     v-text-field(v-model='form.message' label='laisser un message')
     v-btn(@click='submit') submit
</template>

<script lang='coffee'>
export default
     data: ->
          form:
               'form-name': 'un-test'
               message: ''
     methods:
          submit: ->
               @$axios.post '/', @form
                    .then (res) ->
                         alert res
                    .catch (e) ->
                         alert e
                    .then ->
                         'a été appelé'

</script>