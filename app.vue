<template>
  <div class="m-8 font-sans flex justify-center w-full">
    <div class="max-w-screen-sm w-full flex flex-col items-center space-y-4">
      <div class="flex justify-center">
        <h1 class="text-4xl">Todo</h1>
      </div>
      <!-- Create Task -->
      <div class="w-full">
        <div class="bg-gray-300/30 px-4 py-2 border rounded-t-md w-full">
          <p>Add a task</p>
        </div>
        <div class="p-4 border rounded-b-md space-y-2">
          <p>Item</p>
          <input type="text" class="rounded-md border px-4 py-2 w-full text-sm" placeholder="What do you want to do ?">
          <p class="text-sm">Enter what you want to procastinate</p>
          <button class="bg-blue-600 hover:bg-blue-400 text-white text-sm px-3 py-1.5 rounded-md">Submit</button>
        </div>
      </div>
      <!-- Task List -->
      <div class="w-full">
        <div class="bg-gray-300/30 px-4 py-2 border rounded-t-md w-full">
          <p>Tasks</p>
        </div>
        <div class="p-4 border rounded-b-md space-y-2 w-full">
          <table class="w-full table-auto">
            <thead>
              <tr>
                <th>Item</th>
                <th>Status</th>
                <th>Action</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>Buy Benz</td>
                <td>Not Completed</td>
                <td>
                  <button class="bg-blue-600 hover:bg-blue-400 text-white px-3 py-1 rounded-md mr-2">Complete</button>
                  <button class="bg-red-600 hover:bg-red-400 text-white px-3 py-1 rounded-md">Delete</button>
                </td>
              </tr>
              <tr>
                <td>Buy Benz</td>
                <td>Not Completed</td>
                <td>
                  <button class="bg-blue-600 hover:bg-blue-400 text-white px-3 py-1 rounded-md mr-2">Complete</button>
                  <button class="bg-red-600 hover:bg-red-400 text-white px-3 py-1 rounded-md">Delete</button>
                </td>
              </tr>
              <tr>
                <td>Buy Benz</td>
                <td>Not Completed</td>
                <td>
                  <button class="bg-blue-600 hover:bg-blue-400 text-white px-3 py-1 rounded-md mr-2">Complete</button>
                  <button class="bg-red-600 hover:bg-red-400 text-white px-3 py-1 rounded-md">Delete</button>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
  th {
    @apply text-start font-semibold text-sm
  }

  td {
    @apply py-2 text-sm
  }
</style>