<template lang='pug'>
div
    v-dialog(v-model='dialog')
        template(v-slot:activator='{on}')
            v-layout(justify-center)
                v-btn(v-on='on') laisser un message
        v-form(netlify name='ajax' @submit.prevent='onSubmit')
            div(hidden)
                input(name='de')
                input(name='mail')
                textarea(name='message')
            v-container
                v-layout(wrap)
                        v-flex(xs12 md2)
                            v-select(:items='civilItems' label='civilité' v-model='civil')
                        v-flex(xs12 md5)
                            v-text-field(v-model='name' label='name')
                        v-flex(xs12 md5)
                            v-text-field(v-model='email' label='email')

                v-textarea(v-model='message' label='message')
                v-layout(justify-center)
                        v-btn(type='submit') submit
</template>

<script lang='coffee'>
encode = (data) -> ("#{encodeURIComponent key}=#{encodeURIComponent data[key]}" for key of data).join '&'

export default
    data: ->
        # form
        message: ''
        email: ''
        # computed form
        name: ''
        civil: ''
        # other
        dialog: off
        civilItems: ['Madame', 'Monsieur']
    methods:
        onSubmit: ->
            fetch '/',
                method: 'POST'
                headers: 'Content-Type': 'application/x-www-form-urlencoded'
                body: encode {
                    'form-name': 'ajax'
                    de: "#{@civil} #{@name}"
                    mail: @email
                    @message
                }
            @dialog = off
</script>