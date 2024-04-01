<template>
    <div class="container">
        <div class="content">
            <h1>Tạo Liên Hệ Mới</h1>
            <ContactForm :contact="contact" @submit:contact="createContact" />
            <p>{{ message }}</p>
        </div>
    </div>
</template>
  
  <script>
  import ContactForm from "@/components/ContactForm.vue"; // Đảm bảo đường dẫn đúng
  import ContactService from "@/services/contact.service";
  export default {
    components: {
      ContactForm,
    },
    data() {
      return {
        contact: {
          name: "",
          email: "",
          address: "",
          phone: "",
          favorite: false,
        },
        message: "",
      };
    },
    methods: {
        async createContact(contactData) {
            try {
                // Gọi phương thức create của ContactService để thêm liên hệ mới
                await ContactService.create(contactData);
                this.message = "Liên hệ mới đã được tạo và lưu vào cơ sở dữ liệu thành công.";
            } catch (error) {
                console.error("Lỗi khi thêm liên hệ mới:", error);
                this.message = "Đã xảy ra lỗi khi thêm liên hệ mới và lưu vào cơ sở dữ liệu.";
            }
        },
    },
  };
  </script>
  <style>
  .container {
      display: flex;
      justify-content: center;
      align-items: center;
  }
  .form-group {
      width: 300px;
      margin-bottom: 20px; 
  } 
  
  </style>
  