<template>

    <Form @submit="onSubmit" :validation-schema="formSchema">

        <div class="form-group">
            <label for="name">Name</label>
            <Field 
                name="name" 
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
            <Field name="email" v-slot="{field, errors, errorMessage }">

                <input
                    type="text"
                    id="email"
                    class="form-control"
                    v-bind="field"
                    :class="{'is-invalid': errors.length !== 0}"
                />
                <div 
                    class="alert alert-danger" 
                    role="alert"
                    v-if="errors.length !== 0"
                >
                    {{ errorMessage }}
                </div>
            </Field>
        </div>


        <div class="form-group">
            <label for="message">Message</label>
            <Field name="message" v-slot="{ field, errors, errorMessage }">

                <textarea
                    class="form-control"
                    :class="{'is-invalid': errors.length !== 0}"
                    id="message"
                    rows="3"
                    v-bind="field"
                ></textarea>
                <div 
                    class="alert alert-danger" 
                    role="alert"
                    v-if="errors.length !== 0"
                >
                    {{ errorMessage }}
                </div>

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
        data(){
            return {
                formSchema:{
                    name(value){
                        if(value && value.trim()){
                            return true
                        }
                        return  'The name is required'
                    },
                    email(value){
                        if(!value){
                            return 'This email is required';
                        }
                        if(!/^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,4}$/i.test(value)){
                            return 'Bad email'
                        }
                        return true;
                    },
                    message(value){
                        if(!value){
                            return 'The message is required'
                        }
                        return true;
                    }
                }
            }
        },
        methods:{
            onSubmit(values,{ resetForm }){
                console.log(values)
                resetForm();
            }
        }
    }


</script>