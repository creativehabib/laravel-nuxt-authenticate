<script setup>
import InputText from "~/components/Form/inputText.vue";

const form = reactive({
  email: null,
  password: null
})

const handleSubmit = () => {
  console.log(form)
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
              </div>
              <div class="mb-6">
                <FormLabel for="password">Your Password</FormLabel>
                <FormInputText id="password" placeholder="Enter password" v-model="form.password" type="password"/>
              </div>
              <div class="flex items-start mb-6">
                <div class="flex items-center h-5">
                  <input id="remember" type="checkbox" value="" class="w-4 h-4 border border-gray-300 rounded bg-gray-50 focus:ring-3 focus:ring-blue-300 dark:bg-gray-700 dark:border-gray-600 dark:focus:ring-blue-600 dark:ring-offset-gray-800 dark:focus:ring-offset-gray-800" required>
                </div>
                <label for="remember" class="ml-2 text-sm font-medium text-gray-900 dark:text-gray-300">Remember me</label>
              </div>
              <button type="submit" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm w-full sm:w-auto px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">Submit</button>
            </form>
      </div>
    </div>
  </div>
</template>