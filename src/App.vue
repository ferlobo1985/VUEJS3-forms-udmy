<template>
  <app-header></app-header>
        <div class="container">
            <compContact></compContact>
        </div>
    <app-footer></app-footer>
</template>

<script>
  import compContact from './components/contact';

  export default{
    components:{
      compContact
    }
  }
</script>
