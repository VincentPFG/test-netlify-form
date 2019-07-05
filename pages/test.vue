<template lang='pug'>
v-form(netflify @submit.prevent='submit')
     v-text-field(v-model='form.name' label='name')
     v-text-field(v-model='form.email' label='email')
     v-text-field(v-model='form.message' label='message')
     v-text-field(v-model='form.other' label='other')
     v-btn(type='submit') submit
</template>

<script lang='coffee'>
export default
     data: ->
          form:
               'form-name': 'test un'
               name: ''
               email: ''
               message: ''
               other: ''
     methods:
          encode: (data) ->
               ("#{encodeURIComponent key}=#{encodeURIComponent data[key]}" for key of data)
                    .join '&'
          submit: ->
               @$axios.post '/', @encode @form
                    .then (res) ->
                         alert res
                    .catch (e) ->
                         alert e
                    .then ->
                         alert 'a été appelé'
</script>