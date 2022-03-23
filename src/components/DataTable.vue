<template>
  <table class="table-auto border-collapse w-full">
    <thead>
      <tr
        class="rounded-lg text-sm font-medium text-gray-700 text-left"
        style="font-size: 0.9674rem"
      >
        <th class="px-4 py-2 bg-gray-200" v-for="h in header" :key="h.key">{{ h.title }}</th>
        <th class="px-5 py-2 bg-gray-200">Action</th>
      </tr>
    </thead>
    <tbody class="text-sm font-normal text-gray-700">
      <tr
        class="hover:bg-gray-100 border-b border-gray-200 py-10"
        v-for="(d, ti) in data"
        :key="ti"
      >
        <td class="px-4 py-4" v-for="(h, i) in header" :key="i">{{ d[h.key] }}</td>
        <td class="px-4 py-4">
          <div class="flex space-x-2">
            <button
              @click="$emit('delete', d)"
              class="hover:text-gray-100 text-red-600 hover:bg-red-600 rounded"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-6 w-6"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
                stroke-width="2"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16"
                />
              </svg>
            </button>
            <button
              @click="$emit('edit', d)"
              class="hover:text-gray-100 text-green-600 hover:bg-green-600 rounded"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-6 w-6"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
                stroke-width="2"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  d="M11 5H6a2 2 0 00-2 2v11a2 2 0 002 2h11a2 2 0 002-2v-5m-1.414-9.414a2 2 0 112.828 2.828L11.828 15H9v-2.828l8.586-8.586z"
                />
              </svg>
            </button>
          </div>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  name: 'DataTable',
  props: {
    data: { required: true, type: Array },
    header: { required: true, type: Array }
  }
}
</script>

<style>
</style>
