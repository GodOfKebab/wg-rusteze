<template>
  <div class="fixed inset-0 overflow-y-auto">
    <div class="flex items-end justify-center min-h-screen pt-4 px-4 pb-20 text-center sm:block sm:p-0">
      <div aria-hidden="true" class="fixed inset-0 transition-opacity">
        <div class="absolute inset-0 bg-gray-500 opacity-75"></div>
      </div>

      <span aria-hidden="true" class="hidden sm:inline-block sm:align-middle sm:h-screen">&#8203;</span>
      <div
          aria-modal="true"
          class="inline-block align-bottom bg-white rounded-lg text-left overflow-hidden shadow-xl transform transition-all sm:my-8 sm:align-middle sm:max-w-lg sm:w-full"
          role="dialog">
        <div class="bg-white px-4 pt-4 sm:px-6 sm:pt-6">
          <div class="pr-4">
            <div v-if="icon === 'danger'"
                 class="mx-auto flex-shrink-0 flex items-center justify-center h-12 w-12 rounded-full bg-red-100 sm:mx-0 sm:h-10 sm:w-10">
              <!-- Heroicon name: outline/exclamation -->
              <svg aria-hidden="true" class="h-6 w-6 text-red-600" fill="none" stroke="currentColor"
                   viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                <path
                    d="M12 9v2m0 4h.01m-6.938 4h13.856c1.54 0 2.502-1.667 1.732-3L13.732 4c-.77-1.333-2.694-1.333-3.464 0L3.34 16c-.77 1.333.192 3 1.732 3z"
                    stroke-linecap="round" stroke-linejoin="round"
                    stroke-width="2"/>
              </svg>
            </div>
            <div v-else-if="icon === 'add'"
                 class="mx-auto flex-shrink-0 flex items-center justify-center h-12 w-12 rounded-full bg-green-700 sm:mx-0 sm:h-10 sm:w-10">
              <svg class="h-6 w-6 text-white" fill="none" stroke="currentColor"
                   viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                <path d="M12 6v6m0 0v6m0-6h6m-6 0H6" stroke-linecap="round" stroke-linejoin="round"
                      stroke-width="2"/>
              </svg>
            </div>
            <div class="m-2 text-center sm:text-left w-full">
              <slot></slot>
            </div>
          </div>
        </div>
        <div class="bg-gray-50 px-4 py-3 sm:px-6 sm:flex sm:flex-row-reverse">
          <button v-if="rightButtonText" :class="rightButtonClasses" :disabled="rightButtonDisabled"
                  class="w-full inline-flex justify-center rounded-md border border-transparent shadow-sm px-4 py-2  text-base font-medium sm:ml-3 sm:w-auto sm:text-sm"
                  type="button" @click="rightButtonClick">
            {{ rightButtonText }}
          </button>
          <button v-if="leftButtonText" :class="leftButtonClasses" :disabled="leftButtonDisabled"
                  class="mt-3 w-full inline-flex justify-center rounded-md border border-gray-300 shadow-sm px-4 py-2 bg-white text-base font-medium text-gray-700 hover:bg-gray-50 sm:mt-0 sm:ml-3 sm:w-auto sm:text-sm"
                  type="button" @click="leftButtonClick">
            {{ leftButtonText }}
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "custom-dialog",
  props: {
    rightButtonText: {
      type: String,
      default: 'Approve',
    },
    rightButtonClasses: {
      type: Array,
      default: ['text-white', 'bg-green-600', 'hover:bg-green-700'],
    },
    rightButtonDisabled: {
      type: Boolean,
      default: false,
    },
    rightButtonClick: {
      type: Function,
      default: () => {
      },
    },
    leftButtonText: {
      type: String,
      default: 'Cancel',
    },
    leftButtonClasses: {
      type: Array,
      default: [],
    },
    leftButtonDisabled: {
      type: Boolean,
      default: false,
    },
    leftButtonClick: {
      type: Function,
      default: () => {
      },
    },
    icon: {
      type: String,
      default: '',
    },
  }
}
</script>

<style scoped>
</style>