<template>
  <div class="page border">
    <div class="form">
      <h4>Thêm Liên hệ</h4>
      <ContactForm @submit:contact="addContact" />
      <p>{{ message }}</p>
    </div>
  </div>
</template>
<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/services/contact.service";
export default {
  components: {
    ContactForm,
  },

  data() {
    return {
      contact: null,
      message: "",
    };
  },
  methods: {
    async addContact(data) {
      try {
        await ContactService.create(data);
        this.message = "Thêm liên hệ thành công.";
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>
<style scoped>
.border {
  margin: 50px auto;
  border: 2px solid black;
}
.form {
  padding: 10px 20px;
  background-color: aqua;
}
</style>
