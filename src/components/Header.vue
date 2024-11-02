<script setup>
import { ref } from 'vue'
import { Dialog, DialogPanel } from '@headlessui/vue'
import { Bars3Icon, XMarkIcon } from '@heroicons/vue/24/outline'

const links = [
  { text: 'Destinations' },
  { text: 'Features' },
  { text: 'Maps' },
  { text: 'Company' }
]

const mobileMenuOpen = ref(false)
</script>

<template>
  <header class="bg-indigo-900 text-white">
    <nav class="mx-auto flex max-w-7xl items-center justify-between p-6" aria-label="Global">
      <div class="flex lg:flex-1 font-semibold">
        <a href="/">
          <h1 class="text-3xl">TourismApp</h1>
        </a>
      </div>

      <div class="hidden lg:flex lg:gap-x-20">
        <a v-for="link in links" :key="link" href="/" class="font-semibold hover:text-red-500" v-text="link.text" />
      </div>

      <div class="hidden lg:flex lg:flex-1 lg:justify-end">
        <a href="/" class="font-semibold hover:text-red-500">Log in</a>
      </div>

      <div class="flex lg:hidden">
        <button type="button" class="flex rounded-md" @click="mobileMenuOpen = true">
          <span class="sr-only">Open main menu</span>
          <Bars3Icon class="h-6 w-6" aria-hidden="true" />
        </button>
      </div>
    </nav>

    <Dialog class="lg:hidden" @close="mobileMenuOpen = false" :open="mobileMenuOpen">
      <DialogPanel class="fixed inset-y-0 right-0 overflow-y-auto bg-white p-6 ring-1 ring-gray-900/10">
        <div class="flex justify-end">
          <button type="button" class="rounded-md text-gray-700" @click="mobileMenuOpen = false">
            <span class="sr-only">Close menu</span>
            <XMarkIcon class="h-6 w-6" aria-hidden="true" />
          </button>
        </div>

        <div class="py-6 flow-root -my-6 divide-y divide-gray-900">
          <div class="space-y-4 py-6">
            <a v-for="link in links" :key="link" href="/" class="block font-semibold" v-text="link.text" />
          </div>

          <div class="py-6">
            <a href="/" class="font-semibold">Log in</a>
          </div>
        </div>
      </DialogPanel>
    </Dialog>
  </header>
</template>
