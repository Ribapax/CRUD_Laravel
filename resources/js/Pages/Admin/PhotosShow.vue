<template>
  <app-layout title="Edit Photo">
    <template #header>
      <h2 class="font-semibold text-xl text-gray-800 leading-tight">Edit Photo</h2>
    </template>
    <div class="py-12">
      <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
        <form >
          <div>
            <label for="description" class="block text-sm font-medium text-gray-700">Description</label>
            <div class="mt-1">
              <textarea id="description" name="description" rows="3"
                class="shadow-sm focus:ring-indigo-500 focus:border-indigo-500 mt-1 block w-full sm:text-sm border border-gray-300 rounded-md"
                placeholder="lorem ipsum" v-model="form.description"  readonly/>
            </div>
            <p class="mt-2 text-sm text-gray-500">Brief description for your photo</p>
            <div class="text-red-500" v-if="form.errors.description">{{ form.errors.description }}</div>
          </div>

          <div class="grid grid-cols-2">
            <div class="preview p-4">
              <img :src="'/storage/' + photo.path" alt />
            </div>
            
          </div>

        
        </form>
      </div>
    </div>
  </app-layout>
</template>
<script>

import { defineComponent } from "vue";
import AppLayout from "@/Layouts/AppLayout.vue";
import { useForm } from '@inertiajs/vue3';

export default defineComponent({
  components: {
    AppLayout,
  },
  props: {
    photo: Object
  },
  setup(props) {
    const form = useForm({
      //_method: "PUT",
      path: null,
      description: props.photo.description,
    })

    return { form }
  },

});

</script>