<template>
  <div class="relative top-1">
    <div class="bg-white pb-4 px-4 rounded-md w-full">
      <div class="flex justify-between w-full pt-6">
        <input
          type="text"
          class="w-34 h-8 leading-snug border border-gray-300 block appearance-none bg-gray-100 text-sm text-gray-600 py-1 px-2 rounded-lg"
          placeholder="Search"
        />
        <button
          @click="isShowModal = true"
          class="bg-gray-400 hover:bg-gray-200 rounded px-4 py-2"
        >Add Data</button>
      </div>

      <div class="overflow-x-auto mt-6">
        <DataTable
          :data="userList"
          :header="userTableHeader"
          @delete="askDelete($event)"
          @edit="askEdit($event)"
        />
      </div>
    </div>
  </div>

  <div
    class="fixed z-10 inset-0 overflow-y-auto"
    aria-labelledby="modal-title"
    role="dialog"
    aria-modal="true"
    v-if="isShowModal"
  >
    <div
      class="flex items-end justify-center min-h-screen pt-4 px-4 pb-20 text-center sm:block sm:p-0"
    >
      <div
        class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity"
        aria-hidden="true"
        @click="isShowModal = false"
      ></div>

      <span class="hidden sm:inline-block sm:align-middle sm:h-screen" aria-hidden="true">&#8203;</span>

      <div
        class="relative inline-block align-bottom bg-white rounded-lg text-left overflow-hidden shadow-xl transform transition-all sm:my-8 sm:align-middle sm:max-w-lg sm:w-full"
      >
        <div id="edit" class="bg-white px-4 pt-5 pb-4 sm:p-6 sm:pb-4">
          <div class="sm:flex sm:items-start">
            <div class="mt-3 text-center sm:mt-0 sm:ml-4 sm:text-left">
              <div class="mt-2">
                <form @submit.prevent="submit">
                  <h2 class="text-2xl font-bold">Add Data</h2>
                  <hr class="my-6" />
                  <label class="uppercase text-sm font-bold opacity-70">Name</label>
                  <input
                    type="text"
                    :required="true"
                    v-model="fname"
                    class="p-3 mt-2 mb-4 w-full bg-slate-200 rounded border-2 border-slate-200 focus:border-slate-600 focus:outline-none"
                  />
                  <label class="uppercase text-sm font-bold opacity-70">Email</label>
                  <input
                    type="text"
                    :required="true"
                    v-model="email"
                    class="p-3 mt-2 mb-4 w-full bg-slate-200 rounded"
                  />
                  <label class="uppercase text-sm font-bold opacity-70">Gender</label>
                  <select
                    :required="true"
                    v-model="gender"
                    class="p-3 mt-2 mb-4 w-full bg-slate-200 rounded border-2 border-slate-200 focus:border-slate-600 focus:outline-none"
                  >
                    <option value="male">Male</option>
                    <option value="female">Female</option>
                  </select>
                  <div class="px-2 py-3 sm:px-6 sm:flex sm:flex-row-reverse justify-between">
                    <button
                      type="submit"
                      @click="save"
                      class="w-full inline-flex justify-center rounded-md border border-transparent shadow-sm px-4 py-2 bg-green-600 text-base font-medium text-white hover:bg-green-700 sm:ml-3 sm:w-auto sm:text-sm"
                    >Save</button>
                    <button
                      type="button"
                      @click="isShowModal = false"
                      class="w-full inline-flex justify-center rounded-md border border-gray-300 shadow-sm px-4 py-2 bg-white text-base font-medium text-gray-700 hover:bg-gray-50 sm:mt-0 sm:ml-3 sm:w-auto sm:text-sm"
                    >Cancel</button>
                  </div>
                </form>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

import DataTable from '../components/DataTable.vue'

export default {
  data() {
    return {
      fname: '',
      email: '',
      gender: '',
      nextBarId: 2,
      isShowModal: false,
      userTableHeader: [
        { key: 'id', title: 'ID' },
        { key: 'fname', title: 'Нэр' },
        { key: 'email', title: 'Email' },
        { key: 'gender', title: 'Хүйс' }
      ],
      userList: [
        { id: 0, fname: 'Radla', email: 'Amraa@gmail.com', gender: 'male' },
        { id: 1, fname: 'TaycBig', email: 'TaycBig@yahoo.com', gender: 'male' },
      ],
    }
  },
  components: { DataTable },
  methods: {
    save() {
      if (!this.fname || !this.email || !this.gender) {
        return
      }
      this.userList.push({
        id: this.nextBarId++,
        fname: this.fname,
        email: this.email,
        gender: this.gender
      })

      this.fname = '';
      this.email = '';
      this.gender = '';

      this.isShowModal = false;
    },
    askDelete(data) {
      this.userList.splice(this.userList.indexOf(data), 1);
    },

    askEdit(data) {
      this.fname = data.fname;
      this.email = data.email;
      this.gender = data.gender;
      this.isShowModal = true

    },
  }
}
</script>
