<template>
  <app-header></app-header>
        <div class="container">
            <!-- <compContact></compContact> -->
            <comp-validate></comp-validate>
        </div>
    <app-footer></app-footer>
</template>

<script>
  // import compContact from './components/contact';
  import compValidate from './components/Validate';

  export default{
    components:{
      compValidate
    }
  }
</script>
