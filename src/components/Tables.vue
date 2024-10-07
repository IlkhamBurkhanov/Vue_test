<template>
  <div class="bg-[#FFF] p-8 mt-5 rounded-xl">
    <h1 class="text-[#2F2F37] text-xl font-bold pb-3.5 border-b border-[#D7DFED]">
      История звонков
    </h1>
    <div class="overflow-x-auto my-5">
      <table class="min-w-full bg-white border-separate border-spacing-0">
        <thead>
          <tr>
            <th
              class="py-2 w-[60px] px-4 bg-[#EBEFFF] border rounded-tl-[10px] border-gray-200 text-left text-[15px] font-bold text-[#8294AF]"
            >
              №
            </th>
            <th
              class="py-2 w-[294px] px-4 bg-[#EBEFFF] border-y border border-r border-gray-200 text-left text-[15px] font-bold text-[#8294AF]"
            >
              ФИО клиента
            </th>
            <th
              class="py-2 w-[163px] px-4 bg-[#EBEFFF] border-y border-r border-gray-200 text-left text-[15px] font-bold text-[#8294AF]"
            >
              Номер телефона
            </th>
            <th
              class="py-2 w-[112px] px-4 bg-[#EBEFFF] border-y border-r border-gray-200 text-left text-[15px] font-bold text-[#8294AF]"
            >
              Оператор
            </th>
            <th
              class="py-2 w-[178px] px-4 bg-[#EBEFFF] border-y border-r border-gray-200 text-left text-[15px] font-bold text-[#8294AF]"
            >
              Дата и время
            </th>
            <th
              class="py-2 w-[245px] px-4 bg-[#EBEFFF] border-y border-r border-gray-200 text-left text-[15px] font-bold text-[#8294AF]"
            >
              Тип обращения
            </th>
            <th
              class="py-2 w-[260px] px-4 bg-[#EBEFFF] border-y border-r rounded-tr-[10px] border-gray-200 text-left text-[15px] font-bold text-[#8294AF]"
            >
              Примечание
            </th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(user, index) in users" :key="user.id" class="hover:bg-gray-100">
            <td
              class="py-[18px] px-3.5 border-r border-b border-l border-[#D5DCF4] w-[60px]"
              :class="{ 'rounded-bl-[10px]': index === users.length - 1 }"
            >
              {{ index + 1 }}
            </td>
            <td class="py-[18px] px-3.5 border-b border-r border-[#D5DCF4] w-[294px]">
              {{ user.name }}
            </td>
            <td class="py-[18px] px-3.5 border-b border-r border-[#D5DCF4] w-[163px]">
              {{ user.phone }}
            </td>
            <td class="py-[18px] px-3.5 border-b border-r border-[#D5DCF4] w-[112px]">
              {{ user.operator }}
            </td>
            <td class="py-[18px] px-3.5 border-b border-r border-[#D5DCF4] w-[178px]">
              {{ user.date }}
            </td>
            <td class="py-[18px] px-3.5 border-b border-r border-[#D5DCF4] w-[245px]">
              {{ user.tip }}
            </td>
            <td
              class="py-[18px] px-3.5 border-b border-r border-[#D5DCF4] w-[260px]"
              :class="{ 'rounded-br-[10px]': index === users.length - 1 }"
            >
              {{ user.type_pay }}
            </td>
          </tr>
        </tbody>
      </table>
    </div>
    <div class="w-full">
      <button
        @click="sendData"
        class="w-full text-[15px] text-[#1A99FF] font-bold py-2 px-8 border border-[#1A99FF] rounded-xl"
      >
        Загрузить больше
      </button>
    </div>
  </div>
</template>
<script>
import axios from 'axios'

export default {
  data() {
    return {
      token: 'your_token_here',
      users: [
        {
          id: 1,
          name: 'Абдуллаев Абдулла Абдуллаевич',
          phone: '998919884567',
          operator: '1215',
          date: '20.08.2024, 09:12:15',
          tip: 'Информационные запросы',
          type_pay: 'Дебетовые карты'
        },
        {
          id: 2,
          name: 'Jane Smith',
          phone: '998919884567',
          operator: '1215',
          date: '20.08.2024, 09:12:15',
          tip: 'Информационные запросы',
          type_pay: 'Дебетовые карты'
        },
        {
          id: 3,
          name: 'Alice Brown',
          phone: '998919884567',
          operator: '1215',
          date: '20.08.2024, 09:12:15',
          tip: 'Информационные запросы',
          type_pay: 'Дебетовые карты'
        },
        {
          id: 4,
          name: 'Alice Brown',
          phone: '998919884567',
          operator: '1215',
          date: '20.08.2024, 09:12:15',
          tip: 'Информационные запросы',
          type_pay: 'Дебетовые карты'
        },
        {
          id: 5,
          name: 'Абдуллаев Абдулла Абдуллаевич',
          phone: '998919884567',
          operator: '1215',
          date: '20.08.2024, 09:12:15',
          tip: 'Информационные запросы',
          type_pay: 'Дебетовые карты'
        }
      ] // You should replace this with your actual token
    }
  },
  methods: {
    sendData() {
      const dataToSend = 'Hello from Child!'
      // Emit an event named 'send-data' with data
      this.$emit('send-data', dataToSend)
    },
    deleteUser(id) {
      this.users = this.users.filter((user) => user.id !== id)
    },
    // GET Request
    async getData() {
      try {
        const response = await axios.get('https://your-api-url.com/api/data', {
          headers: {
            Authorization: `Bearer ${this.token}`
          }
        })
        console.log('GET Response:', response.data)
      } catch (error) {
        console.error('Error fetching data:', error)
      }
    },

    // POST Request
    async postData(payload) {
      try {
        const response = await axios.post('https://your-api-url.com/api/data', payload, {
          headers: {
            Authorization: `Bearer ${this.token}`
          }
        })
        console.log('POST Response:', response.data)
      } catch (error) {
        console.error('Error posting data:', error)
      }
    },

    // PUT Request
    async updateData(id, updatedData) {
      try {
        const response = await axios.put(`https://your-api-url.com/api/data/${id}`, updatedData, {
          headers: {
            Authorization: `Bearer ${this.token}`
          }
        })
        console.log('PUT Response:', response.data)
      } catch (error) {
        console.error('Error updating data:', error)
      }
    },

    // DELETE Request
    async deleteData(id) {
      try {
        const response = await axios.delete(`https://your-api-url.com/api/data/${id}`, {
          headers: {
            Authorization: `Bearer ${this.token}`
          }
        })
        console.log('DELETE Response:', response.data)
      } catch (error) {
        console.error('Error deleting data:', error)
      }
    }
  }
}
</script>
