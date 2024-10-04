<template>
  <div class="flex justify-between gap-8 items-center bg-[#FFF] rounded-xl mt-2 py-5 px-8">
    <div class="flex items-center gap-3">
      <!-- Avatar 1 -->
      <div class="relative inline-block">
        <!-- Circular Avatar -->
        <img
          src="https://images.unsplash.com/photo-1491528323818-fdd1faba62cc?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
          alt="Avatar"
          class="h-11 w-11 rounded-full object-cover"
        />

        <!-- Little image instead of notification dot -->
        <img
          src="../assets/Icons/russia.svg"
          alt="Notification Icon"
          class="absolute bottom-0 right-0 h-3.5 w-3.5 rounded-full border-2 border-white"
        />
      </div>
      <div>
        <h1 class="">Abdullaev Abdulla Abdullaevich</h1>
        <p class="text-[#8294AF] text-[13px]">Русский язык</p>
      </div>
    </div>
    <div class="flex gap-5 items-center">
      <div v-for="(item, index) in datas" :key="index" class="flex flex-col">
        <h2 class="text-[#8294AF] text-[13px]">{{ item?.title }}</h2>
        <p class="text-[#2F2F37] text-sm">{{ item?.item }}</p>
      </div>
    </div>
    <div class="flex gap-4">
      <div
        class="flex items-center gap-[7px] py-[7px] px-2.5 border border-[#CAE9DE] rounded-[50px] bg-[#F5FFFB]"
      >
        <h2 class="h-3 w-3 bg-[#44C395] rounded-full border-2 border-white"></h2>
        <p class="text-[#44C395] text-sm font-medium">00:10</p>
      </div>
      <div class="flex gap-1.5">
        <div @click="handleClick" class="border rounded-full bg-[#FF6E41]">
          <img
            class="inline-block h-5 w-5 my-[8px] mx-[8px] ring-2 ring-[#FF6E41]"
            src="../assets/Icons/EndCalling.svg"
            alt=""
          />
        </div>
        <div class="border rounded-full">
          <img
            class="inline-block h-4 w-4 my-[10px] mx-[10px] ring-2 ring-white"
            src="../assets/Icons/Pause.svg"
            alt=""
          />
        </div>
        <div class="border rounded-full">
          <img
            class="inline-block h-4 w-4 my-[10px] mx-[10px] ring-2 ring-white"
            src="../assets/Icons/Microfon.svg"
            alt=""
          />
        </div>
        <div class="border rounded-full">
          <img
            class="inline-block h-4 w-4 my-[10px] mx-[10px] ring-2 ring-white"
            src="../assets/Icons/Message.svg"
            alt=""
          />
        </div>
        <div class="border rounded-full">
          <img
            class="inline-block h-4 w-4 my-[10px] mx-[10px] ring-2 ring-white"
            src="../assets/Icons/AddCalling.svg"
            alt=""
          />
        </div>
      </div>
      <div class="flex items-center border border-[#1A99FF] rounded-xl max-w-[140px] px-3 py-2">
        <!-- Search Icon -->
        <img src="../assets/Icons/Search.svg" alt="Search Icon" class="w-4.5 h-4.5" />

        <!-- Search Input -->
        <input
          type="text"
          placeholder="Поиск клиента"
          @input="handleInput"
          class="flex-grow outline-none max-w-[100px] bg-transparent placeholder:text-[#1A99FF] text-sm"
        />
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Calling',
  data() {
    return {
      // Define your array here
      datas: [
        {
          title: 'ПИНФЛ',
          item: '30101800050014'
        },
        {
          title: 'Дата рождения',
          item: '01.01.2000'
        },
        {
          title: 'Номер телефона',
          item: '+998 91 2345678'
        },
        {
          title: 'Тип',
          item: 'Физ. лицо'
        }
      ]
    }
  },
  methods: {
    handleClick() {
      console.log('clicked in vue')
    },
    handleInput(event) {
      console.log(event.target.value)
    }
  }
}
</script>
