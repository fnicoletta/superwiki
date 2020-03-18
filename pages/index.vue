<template>
   <div>
      <Navbar />
      <Modal />
   </div>
</template>

<script>
   import Modal from '@/components/modal.vue'
   import Navbar from '@/components/navbar.vue'
   export default {
      data() {
         return {}
      },
      components: {
         Modal,
         Navbar,
      },

      computed: {
         console: () => console,
      },
   }
</script>

<style></style>
