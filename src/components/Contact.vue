<template>
  <section id="contact" class="pt-20 pb-32">
    <div class="contact__container">
      <h2 class="md:justify-center after:w-20">
        {{ $t("contact.title") }}
      </h2>
      <form @submit.prevent="sendEmail" class="contact__form">
        <input
          type="text"
          v-model="form.name"
          :placeholder="$t('contact.form.name')"
          required
        />
        <input
          type="email"
          v-model="form.email"
          :placeholder="$t('contact.form.email')"
          required
        />
        <textarea
          v-model="form.message"
          :placeholder="$t('contact.form.message')"
          required
          rows="5"
        ></textarea>
        <DialogModal
          :isOpen="isOpen"
          :title="success ? $t('contact.form.successTitle') : $t('contact.form.errorTitle')"
          :description="status"
          :success="success"
          @close="isOpen = false"
        />
      </form>
    </div>
  </section>
</template>

<script>
import emailjs from "emailjs-com";
import DialogModal from "./DialogModal.vue";
export default {
  name: "Contact",
  components: {
    DialogModal,
  },
  data() {
    return {
      form: {
        name: "",
        email: "",
        message: "",
      },
      status: "",
      success: false,
      isOpen: false,
    };
  },
  methods: {
    sendEmail() {
      const userID = import.meta.env.VITE_EMAILJS_USER_ID;
      const serviceID = import.meta.env.VITE_EMAILJS_SERVICE_ID;
      const templateID = import.meta.env.VITE_EMAILJS_TEMPLATE_ID;

      emailjs.init(userID);
      emailjs
        .send(serviceID, templateID, this.form)
        .then(() => {
          this.status = this.$t("contact.form.successStatus");
          this.success = true;
          this.isOpen = true;
          this.form = { name: "", email: "", message: "" };
        })
        .catch((error) => {
          this.status = this.$t("contact.form.errorStatus");
          this.success = false;
          console.error("Error sending email", error);
        });
    },
  },
};
</script>

<style scoped>
.contact__container {
  @apply max-w-screen-sm m-auto;
}
.contact__form {
  @apply flex flex-col gap-5 p-2 md:p-5 bg-yellow-200 shadow-2xl rounded-md;
}
.contact__button {
  @apply border-2 rounded-md w-max self-end py-2 px-12 bg-gray-700 border-black font-semibold transition-all duration-500;
  @apply hover:border-fuchsia-950 hover:bg-orange-400 hover:text-fuchsia-950;
}
</style>
