<template>
  <div class="flex justify-between items-center px-8 bg-white">
    <div>
      <img src="../assets/Logos/Logo1.svg" />
    </div>
    <div class="flex text-base">
      <!-- Button 1 -->
      <button
        :class="{
          'bg-[#F3FAFF] text-black font-bold border-b-[3px] border-[#1A99FF]': activeButton === 1,
          ' text-[#8294AF]': activeButton !== 1
        }"
        class="px-4 py-7 transition duration-300"
        @click="setActive(1)"
      >
        Обращение клиента
      </button>

      <!-- Button 2 -->
      <button
        :class="{
          'bg-[#F3FAFF] text-black font-bold  border-b-[3px] border-[#1A99FF]': activeButton === 2,
          ' text-[#8294AF]': activeButton !== 2
        }"
        class="px-4 py-7 transition duration-300"
        @click="setActive(2)"
      >
        Продукты клиента
      </button>
    </div>
    <div class="flex items-center gap-6">
      <div class="flex border border-[#EBEFFF] rounded-[50px] gap-[7px] py-2 px-3">
        <img src="../assets/Icons/Group1.svg" alt="" />
        <div>
          <h2 class="text-[#1A99FF] text-[10px]">Ожидание</h2>
          <div class="flex items-center gap-0.5">
            <h3 class="text-lg font-bold text-[#2F2F37]">106</h3>
            <p class="text-[#8294AF] text-[10px]">(18:08)</p>
          </div>
        </div>
        <img src="../assets/Icons/Frame.svg" alt="" />
      </div>
      <div class="flex gap-4 overflow-hidden">
        <div>
          <h2 class="text-[15px] font-bold text-[#2F2F37]">Зухра Умарова</h2>
          <p class="text-[10px] font-medium text-right text-white">
            <span class="bg-[#1A99FF] rounded-s-[10px] rounded-br-[10px] px-[5px] pt-0.5 pb-[1px]"
              >Оператор 228</span
            >
          </p>
        </div>
        <div class="relative">
          <img
            src="https://images.unsplash.com/photo-1491528323818-fdd1faba62cc?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
            alt="Avatar"
            class="inline-block h-9 w-9 rounded-full ring-2 ring-white"
          />
          <span
            class="absolute bottom-0 right-0 h-2.5 w-2.5 bg-[#44C395] rounded-full border-2 border-white"
          ></span>
        </div>

        <div class="border rounded-full">
          <img
            class="inline-block h-4 w-4 my-[10px] mx-[10px] ring-2 ring-white"
            src="../assets/Icons/Pod.svg"
            alt=""
          />
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { ref } from 'vue'

export default {
  setup() {
    // Manage the active button state
    const activeButton = ref(1) // Default active button is 1

    // Function to set the active button
    const setActive = (buttonNumber) => {
      activeButton.value = buttonNumber
    }

    return {
      activeButton,
      setActive
    }
  }
}
</script>
