<template>
  <div class="page">
    <h4>Thêm Liên hệ</h4>
    <ContactForm
      :contact="newContact"
      @submit:contact="addContact"
    />
  </div>
</template>
<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/services/contact.service";
export default {
  components: { ContactForm },
  data() {
    return {
      newContact: {
        name: "",
        email: "",
        address: "",
        phone: "",
        favorite: false,
      },
    };
  },
  methods: {
    async addContact(contact) {
      try {
        await ContactService.create(contact);
        alert("Thêm liên hệ thành công!");
        this.$router.push({ name: "contactbook" });
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>
<style scoped>
.page {
  max-width: 600px;
  margin: 0 auto;
}
</style>
