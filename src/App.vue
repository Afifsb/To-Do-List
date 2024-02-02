<script setup lang="ts">
import { ref } from "vue";

let item = ref("");
let itemList = ref([]);
let isCheckedList = ref([]);

function addItem() {
  itemList.value.push(item.value);
  isCheckedList.value.push(false);
  item.value = "";
}

function deleteItem(index) {
  itemList.value.splice(index, 1);
  isCheckedList.value.splice(index, 1);
}
</script>

<template>
  <div class="w-screen h-screen flex justify-center items-center">
    <div class="border border-solid border-black w-[350px] h-[500px]">
      <div>
        <p class="flex justify-center items-center font-semibold h-10">TO DO LIST</p>
      </div>
      <div>
        <input
          type="text"
          name="input"
          id="input1"
          placeholder="Enter itinerary"
          class="border border-solid border-black m-4 rounded-md"
          v-model="item"
        />
        <button
          class="border border-solid border-black rounded-md p-2 m-4 bg-green-600 text-white"
          @click="addItem"
          :disabled="!item"
        >
          Add Item
        </button>
      </div>
      <div>
        <table class="m-5 fixed">
          <tr>
            <th>List of items</th>
          </tr>

          <tr v-for="(itemListAll, index) in itemList" :key="index">
            <td>
              <input type="checkbox" v-model="isCheckedList[index]" />
              <span :style="{ 'text-decoration': isCheckedList[index] ? 'line-through' : 'none' }">{{ itemListAll }}</span>
            </td>

            <td>
              <button class="border border-solid border-black bg-green-500 text-white p-1 ml-4" @click="deleteItem(index)">
                Delete
              </button>
            </td>
          </tr>
        </table>
      </div>
    </div>
  </div>
</template>
