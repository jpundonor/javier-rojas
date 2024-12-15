<template>
  <button type="submit" class="contact__button">
    {{ $t("contact.form.send") }}
  </button>

  <TransitionRoot appear :show="isOpen" as="template">
    <Dialog as="div" @close="closeModal" class="relative z-50">
      <TransitionChild
        as="template"
        enter="duration-300 ease-out"
        enter-from="opacity-0"
        enter-to="opacity-100"
        leave="duration-200 ease-in"
        leave-from="opacity-100"
        leave-to="opacity-0"
      >
        <div class="fixed inset-0 bg-black/25" />
      </TransitionChild>

      <div class="fixed inset-0 overflow-y-auto">
        <div
          class="flex min-h-full items-center justify-center p-4 text-center"
        >
          <TransitionChild
            as="template"
            enter="duration-300 ease-out"
            enter-from="opacity-0 scale-95"
            enter-to="opacity-100 scale-100"
            leave="duration-200 ease-in"
            leave-from="opacity-100 scale-100"
            leave-to="opacity-0 scale-95"
          >
            <DialogPanel class="modal__container">
              <DialogTitle as="h3" :class="`modal__title ${success ? 'text-green-500' : 'text-red-500'}`">
                {{ title }}
              </DialogTitle>
              <div class="mt-2">
                <p class="text-sm text-gray-500">
                  {{ description }}
                </p>
              </div>

              <div class="mt-4">
                <button type="button" class="modal__button" @click="closeModal">
                    {{ $t("contact.form.close") }}
                </button>
              </div>
            </DialogPanel>
          </TransitionChild>
        </div>
      </div>
    </Dialog>
  </TransitionRoot>
</template>

<script>
import {
  TransitionRoot,
  TransitionChild,
  Dialog,
  DialogPanel,
  DialogTitle,
} from "@headlessui/vue";

export default {
  components: {
    TransitionRoot,
    TransitionChild,
    Dialog,
    DialogPanel,
    DialogTitle,
  },
  props: {
    isOpen: Boolean,
    title: String,
    description: String,
    success: Boolean,
  },
  methods: {
    closeModal() {
      this.$emit("close")
    },
  },
  emits: ["close"],
};
</script>

<style scoped>
.contact__button {
  @apply border-2 rounded-md w-max self-end py-2 px-12 bg-gray-700/80 border-black font-semibold transition-all duration-500;
  @apply hover:border-fuchsia-950 hover:bg-orange-400 hover:text-fuchsia-950;
}
.modal__container {
  @apply w-full max-w-md transform overflow-hidden rounded-2xl bg-white p-6 text-left align-middle shadow-xl transition-all;
}
.modal__title {
  @apply text-lg font-medium leading-6;
}
.modal__button {
  @apply inline-flex justify-center rounded-md border border-transparent bg-slate-100 px-4 py-2 text-sm font-medium text-fuchsia-950;
  @apply hover:bg-slate-200 focus:outline-none focus-visible:ring-2 focus-visible:ring-fuchsia-950 focus-visible:ring-offset-2;
}
</style>
