<template>

    <Form>

        <div class="form-group">
            <label for="name">Name</label>
            <Field 
                name="name" 
                :rules="validateName"
                placeholder="Enter your name"
                class="form-control"
            />
            <ErrorMessage name="name" as="div" v-slot="{ message }">
                <div class="alert alert-danger" role="alert">
                    {{ message }}
                </div>
            </ErrorMessage>
        </div>


        <div class="form-group">
            <label for="email">Email</label>
            <Field name="email" :rules="validateEmail" v-slot="{field, errors }">

                <input
                    type="text"
                    id="email"
                    class="form-control"
                    v-bind="field"
                    :class="{'is-invalid': errors.length !== 0}"
                />
            </Field>


        </div>


    
        <hr/>
        <button
          class="btn btn-primary"
        >
          Submit
        </button>

    </Form>

</template>

<script>
    import { Field, Form, ErrorMessage } from 'vee-validate'

    export default {
        components:{
            Field,
            Form,
            ErrorMessage
        },
        methods:{
            isRequired(value){
                if(!value){
                    return 'The field is required'
                }
                return true;
            },
            validateName(value){
                if(value && value.trim()){
                    return true
                }
                return  'The name is required'
            },
            validateEmail(value){
                if(!value){
                    return 'This email is required';
                }
                if(!/^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,4}$/i.test(value)){
                    return 'Bad email'
                }
                return true;
            }
        }
    }


</script>