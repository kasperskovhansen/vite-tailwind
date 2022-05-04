<script setup lang="ts">
import { ref } from "vue";

type UserData = {
  email: string;
  avatar: string;
  first_name: string;
  last_name: string;
  bio: string;
};

const loadUserData = (): Promise<UserData> => {
  return new Promise<any>((resolve, reject) => {
    let userData: UserData;
    const userId = Math.floor(Math.random() * 11) + 1;
    const delay = Math.floor(Math.random() * 2);

    // Fetch general user data
    fetch(`https://reqres.in/api/users/${userId}?delay=${delay}`)
      .then((response) => response.json())
      .then(({ data }) => {
        userData = data;
        return;
      })
      .then(() => {
        // Enrich with bio (bacon ipsum)
        return fetch(
          "https://baconipsum.com/api/?paras=5&type=all-meat&start-with-lorem=1"
        );
      })
      .then((response) => response.json())
      .then((data) => {
        userData.bio = data[0];
        return resolve(userData);
      });
  });
};
const userData = await ref(await loadUserData());

const imgNeedsPaddingTop = ref(true);
const onImageLoaded = () => {
  imgNeedsPaddingTop.value = false;
};
</script>

<template>
  <div class="w-full max-w-screen-sm m-auto p-3 min-h-100 overflow-hidden">
    <div class="wrapper bg-white flex flex-row p-3 rounded-3xl shadow-md">
      <div class="w-1/6 flex-grow-0">
        <div
          class="rounded-full w-full h-auto border-green-700 border-4 p-1 overflow-hidden"
        >
          <img
            class="rounded-full w-full"
            :style="{ 'padding-top': imgNeedsPaddingTop ? '100%' : '0' }"
            :src="userData.avatar"
            alt=""
            @load="onImageLoaded"
          />
        </div>
      </div>
      <div class="w-5/6 info text-left pl-3 text-gray-500">
        <div class="written-by uppercase text-gray-400 tracking-wide text-sm">
          Written by
        </div>
        <div class="name font-bold py-1">
          {{ userData.first_name }} {{ userData.last_name }}
        </div>
        <div class="bio text-sm">{{ userData.bio }}</div>
      </div>
    </div>
  </div>
</template>
