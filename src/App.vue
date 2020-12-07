<template>
    <div class="wrapper">
      <div class="wrapper-content">
        
        <section>
          <div class="container">
            <!-- fisrt button -->
            <button class="btn btnPrimary" @click="modalFirst = !modalFirst">Show first modal</button>
            <!-- fisrt modal -->
            <modals title="First modal"
            v-show="modalFirst"
            @close="modalFirst = false">
            <div slot="body">
              <p>Text text text text text</p>
              <button class="btn btnPrimary" @click="modalFirst = !modalFirst.show">Well Done!</button>
            </div>
            </modals>

            <!-- second button -->
            <button class="btn btnPrimary" @click="modalSecond.show = !modalSecond.show">Show second modal</button>
            <!-- second modal -->
            <modals title="Modal with form"
            v-show="modalSecond.show"
            @close="modalSecond.show = false">
            <div slot="body">
              <form @submit.prevent="submitMethodForm">
                <label>Name:</label>
                <input type="text" required v-model="modalSecond.name">
                <label>Email:</label>
                <input type="email" required v-model="modalSecond.email">
                <button class="btn btnPrimary">Submit!</button>
              </form>
            </div>
            </modals>

          <!-- modal with Validate -->
          <button class="btn btnPrimary" @click="modalValidate = !modalValidate">Show second modal + Validate</button>
          <modalValidate v-show="modalValidate" @close="modalValidate = false" />

          </div>
        </section>
        
      </div>
    </div>
</template>

<script>
import modals from "@/components/UI/Modal.vue";
import modalValidate from "@/components/ModalValidate.vue";

export default {
  components: { modals, modalValidate },
  data () {
    return {
      modalFirst: false,
      modalSecond: {
        show: false,
        name:'',
        email:'',
      },
      modalValidate: false
    }
  },
  methods: {
    submitMethodForm () {
      console.log({
        name: this.modalSecond.name,
        email: this.modalSecond.email
      })
      this.modalSecond.name = '',
      this.modalSecond.email = '',
      this.modalSecond.show = false
    }
  }
};
</script>

<style>
</style>
