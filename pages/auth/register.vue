<script setup>
const auth = useAuthStore();

definePageMeta({
  middleware: ['guest']
})

const form = reactive({
  name: null,
  email: null,
  password: null,
  password_confirmation: null,
})
const errors = ref([])
const handleSubmit = async () => {
  try {
    await auth.register(form)
  } catch (error) {
    errors.value = error.data.errors;
  }
}
</script>
<template>
  <div class="min-h-screen flex items-center">
    <div class="w-full">
      <div class="card bg-white p-8 rounded-lg shadow-xl md:w-3/4 mx-auto lg:w-1/3">
        <h3 class="text-center text-2xl font-semibold">User Register</h3>
          <form @submit.prevent="handleSubmit">
              <div class="mb-6">
                <FormLabel for="name">Name</FormLabel>
                <FormInputText id="name" placeholder="Your name" v-model="form.name" type="text"/>
                <span v-if="errors.name" class="text-red-700 text-sm">{{ errors.name[0] }}</span>
              </div>
              <div class="mb-6">
                <FormLabel for="email">Your Email</FormLabel>
                <FormInputText id="email" placeholder="Email address" v-model="form.email" type="email"/>
                <span v-if="errors.email" class="text-red-700 text-sm">{{ errors.email[0] }}</span>
              </div>
              <div class="mb-6">
                <FormLabel for="password">Your Password</FormLabel>
                <FormInputText id="password" placeholder="Enter password" v-model="form.password" type="password"/>
                <span v-if="errors.password" class="text-red-700 text-sm">{{ errors.password[0] }}</span>
              </div>
              <div class="mb-6">
                <FormLabel for="password_confirmation">Password Confirmation</FormLabel>
                <FormInputText id="password_confirmation" placeholder="Enter confirm password" v-model="form.password_confirmation" type="password"/>
                <span v-if="errors.password_confirmation" class="text-red-700 text-sm">{{ errors.password_confirmation[0] }}</span>
              </div>
              <ButtonPrimary>Register</ButtonPrimary>
          </form>
      </div>
    </div>
  </div>
</template>