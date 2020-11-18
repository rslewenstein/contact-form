<template>
    <v-form
        ref="form"
        v-model="valid"
        lazy-validation
    >

        <v-text-field 
            v-model="name"
            :counter="25"
            :rules="nameRules"
            label="Name"
            required
        ></v-text-field>

        <v-text-field 
            v-model="email"
            :rules="emailRules"
            label="E-mail"
            required
        ></v-text-field>

        <v-select 
            v-model="select"
            :items="countries"
            :rules="[v => !!v || 'Country required']"
            label="Country"
            required
        ></v-select>

        <v-checkbox 
            v-model="checkbox"
            :rules="[v => !!v || 'You must agree to continue!']"
            label="Do you agree?"
            required
        ></v-checkbox>  

        <v-btn 
            :disabled="!valid"
            color="success"
            class="mr-4"
            @click="send"
        >
            Send
        </v-btn>

        <v-btn 
            color="error"
            class="mr-4"
            @click="reset"
        >
            Reset
        </v-btn>   
    </v-form>
</template>

<script>
export default {
    // name: 'Form',
    data: () => ({
        valid: true,
        name: '',
        nameRules: [
            v => !!v || 'Named is required',
            v => (v && v.length <= 10) || 'Name must be less than 10 characters',
        ],
        email: '',
        emailRules: [
            v => !!v || 'Named is required',
            v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
        ],
        select: null,
        countries : [
            'Angola',
            'Argentina',
            'Australia',
            'Belgium',
            'Brazil',
            'Denmark',
            'France',
            'Germany',
            'Portugal'
        ],
        checkbox: false,
    }),

    methods: {
        send (){
           if (this.$refs.form.validate()){
               console.log(this.name + ', ' + this.email + ', ' + this.select)
               alert('Success!')
           } 
            
        },
        reset (){
            this.name = '',
            this.email = '',
            this.select = null,
            this.checkbox = false
        },
    },
}
</script>

<style scoped>
form{
    max-width: 600px;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    margin-left: 25%;
    margin-top: 5%;
    padding: 5px;
    text-align: center;
}
</style>