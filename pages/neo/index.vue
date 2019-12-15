<template lang='pug'>
div
    p {{postForm.intro}}
    v-dialog(v-model='dialog')
        template(v-slot:activator='{on}')
            v-layout(justify-center)
                v-btn(v-on='on') laisser un message
        v-form(netlify name='test-block')
            div(hidden)
                input(name='form-name' value='test-block')
                //- input(name='message' v-model='form.message')
                //- input(name='name' v-model='form.name')
                //- input(name='email' v-model='form.email')
                input(name='intro' :value='postForm.intro')
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
    computed: postForm: -> intro: "#{@form.civil} #{@form.name}"
    methods:
        encode: (data) -> ("#{encodeURIComponent key}=#{encodeURIComponent data[key]}" for key of data).join '&'
        submit: ->
            fetch '/',
                method: 'POST'
                headers: 'Content-Type': 'application/x-www-form-urlencoded'
                body: @encode @postForm
            .then -> alert 'success'
            .error -> alert 'failure'
</script>