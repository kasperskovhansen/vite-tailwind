<template>
  <div class="w-full max-w-screen-sm m-auto p-3 min-h-100 overflow-hidden">
    <div class="wrapper bg-white flex flex-row p-3 rounded-3xl shadow-md">
      <div class="w-1/6 flex-grow-0">
        <div
          class="rounded-full w-full h-auto border-green-700 border-4 p-1 overflow-hidden"
        >
          <img
            class="rounded-full skeleton w-full"
            style="padding-top: 100%"
            alt=""
          />
        </div>
      </div>
      <div class="w-5/6 info text-left pl-3 text-gray-500">
        <div
          class="written-by skeleton bg-gray-200 my-1 w-1/4 h-5 uppercase text-gray-400 tracking-wide text-sm"
        ></div>
        <div
          class="name skeleton bg-gray-200 my-2 w-1/2 h-6 font-bold py-1"
        ></div>
        <div class="bio skeleton bg-gray-200 my-1 w-5/6 h-4 text-sm"></div>
      </div>
    </div>
  </div>
</template>
<style scoped>
.avatar {
  background-image: url("https://picsum.photos/200/200");
}
.skeleton {
  @apply: bg-gray-300;
  animation: skeleton-pulse 4s infinite;
}
@keyframes skeleton-pulse {
  0% {
    @apply bg-gray-50;
  }
  50% {
    @apply bg-gray-300;
  }
  100% {
    @apply bg-gray-50;
  }
}
</style>
