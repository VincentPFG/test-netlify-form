<template lang='pug'>
div
    v-dialog(v-model='dialog')
        template(v-slot:activator='{on}')
            v-layout(justify-center)
                v-btn(v-on='on') laisser un message
        v-form(netlify name='static')
            div(hidden)
                input(name='form-name' value='static')
                input(name='de' :value='intro')
                input(name='mail' :value='email')
                textarea(name='message' :value='message')
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
    computed:
        intro: -> "#{@civil} #{@name}"
</script>