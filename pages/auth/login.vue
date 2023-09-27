<script setup>
const auth = useAuthStore();

definePageMeta({
  middleware: ['guest']
});

const form = reactive({
  email: 'test@example.com',
  password: 'password'
})
const errors = ref([])
const handleSubmit = async () => {
  try {
    await auth.login(form)
  } catch (error) {
    errors.value = error.data.errors;
  }
}
</script>
<template>
  <div class="min-h-screen flex items-center">
    <div class="w-full">
        <div class="card bg-white p-8 rounded-lg shadow-xl md:w-3/4 mx-auto lg:w-1/3">
          <h3 class="text-center text-2xl font-semibold">User login</h3>
            <form @submit.prevent="handleSubmit">
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
              <div class="flex items-start mb-6">
                <div class="flex items-center h-5">
                  <input id="remember" type="checkbox" value="" class="w-4 h-4 border border-gray-300 rounded bg-gray-50 focus:ring-3 focus:ring-blue-300 dark:bg-gray-700 dark:border-gray-600 dark:focus:ring-blue-600 dark:ring-offset-gray-800 dark:focus:ring-offset-gray-800">
                </div>
                <label for="remember" class="ml-2 text-sm font-medium text-gray-900 dark:text-gray-300">Remember me</label>
              </div>
              <ButtonPrimary>Login</ButtonPrimary>
            </form>
      </div>
    </div>
  </div>
</template>