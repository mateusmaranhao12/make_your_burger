<template>
  <Banner />
  <div class="main-container">
    <h1>Monte seu Burger</h1>
    <BurgerForm />
  </div>
  <Footer></Footer>
</template>

<script>

  import BurgerForm from '@/components/BurgerForm.vue'
  import Banner from '@/components/Banner.vue'
  import Footer from '@/components/Footer.vue'

  export default {
    name: 'Home',
    components: {
      Banner,
      BurgerForm,
      Footer
    }
  }

</script>
