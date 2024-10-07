<template>
  <div class="bg-white p-8 rounded-xl">
    <h1 class="text-xl text-[#2F2F37] font-bold pb-3.5 border-b border-[#D7DFED] my-5">
      Обращение клиента
    </h1>
    <div>
      <p class="text-[#8294AF] text-sm">ФИО клиента</p>
      <input
        type="text"
        v-model="inputValue"
        @input="logValue"
        class="w-full border border-gray-300 rounded-lg outline-none py-3 px-2.5 mt-1.5 text-[15px]"
        placeholder="Написать текст..."
      />
    </div>
    <div class="flex gap-[18px] bg-[#F9FAFF] rounded-xl p-5 mt-5 justify-between">
      <!-- Card 1 -->
      <div class="card flex-1">
        <h2 class="text-sm text-[#8294AF]">Тема обращения</h2>
        <div class="space-y-2 bg-[#FFF] h-[234px] p-5 rounded-lg border border-[#D5DCF4] mt-2">
          <!-- Radio Option 1 -->
          <label v-for="(option, index) in options" :key="index" class="flex items-center gap-2.5">
            <input
              type="radio"
              :name="option.name"
              :value="option.value"
              v-model="selectedOption"
              class="form-radio text-blue-600 h-4 w-4"
            />

            <!-- Span text changes color based on selectedOption -->
            <span
              class="ml-2 font-medium"
              :class="{
                'text-[#1A99FF]': selectedOption === option.value, // Blue for selected
                'text-[#2F2F37]': selectedOption !== option.value // Gray for unselected
              }"
            >
              {{ option.label }}
            </span>
          </label>
        </div>
      </div>

      <!-- Card 2 -->
      <div class="card flex-1">
        <h2 class="text-sm text-[#8294AF]">Подтема</h2>
        <div class="space-y-2 bg-[#FFF] h-[234px] p-5 rounded-lg border border-[#D5DCF4] mt-2">
          <!-- Radio Option 1 -->
          <label
            v-for="(optiony, index) in options2"
            :key="index"
            class="flex items-center gap-2.5"
          >
            <input
              type="radio"
              :name="optiony.name"
              :value="optiony.value"
              v-model="selectedOption2"
              class="form-radio text-blue-600 h-4 w-4"
            />

            <!-- Span text changes color based on selectedOption -->
            <span
              class="ml-2 font-medium"
              :class="{
                'text-[#1A99FF]': selectedOption2 === optiony.value, // Blue for selected
                'text-[#2F2F37]': selectedOption2 !== optiony.value // Gray for unselected
              }"
            >
              {{ optiony.label }}
            </span>
          </label>
        </div>
      </div>

      <!-- Card 3 -->
      <div class="card flex-1">
        <h2 class="text-sm text-[#8294AF]">Описание</h2>
        <div class="space-y-2 bg-[#FFF] h-[234px] p-5 rounded-lg border border-[#D5DCF4] mt-2">
          <p class="text-[15px text-[#2F2F37]">UZCARD DUO (RU)</p>
          <a
            href="https://aloqabank.uz/ru/private/plastic-cards/list/uzcard/"
            target="_blank"
            class="text-[#2FB1EA] hover:underline"
          >
            https://aloqabank.uz/ru/private/plastic-cards/list/uzcard/
          </a>
          <p class="text-[15px text-[#2F2F37] pt-5">UZCARD DUO (UZ)</p>
          <a
            href="https://aloqabank.uz/ru/private/plastic-cards/list/uzcard/"
            target="_blank"
            class="text-[#2FB1EA] hover:underline"
          >
            https://aloqabank.uz/ru/private/plastic-cards/list/uzcard/
          </a>
        </div>
      </div>
    </div>
    <div class="my-5">
      <h1 class="text-[#2F2F37] text-lg font-bold">Тип обращения</h1>
      <div class="flex flex-col">
        <div class="flex flex-row flex-wrap mt-0.5 items-start">
          <label
            v-for="(item, index) in options3"
            :key="index"
            class="flex mt-2.5 items-center w-60"
          >
            <input
              type="radio"
              :value="item.label"
              v-model="selectedOption3"
              class="form-radio h-4 w-4 text-blue-600 border-gray-300"
              @change="handleRadioChange"
            />
            <span
              class="ml-2 text-[15px] w-[200px]"
              :class="{
                'text-[#1A99FF]': selectedOption3 === item.label,
                'text-black': selectedOption3 !== item.label
              }"
            >
              {{ item.label }}
            </span>
          </label>
        </div>
      </div>
    </div>
    <div>
      <p class="text-[#8294AF] text-sm">Примечание</p>
      <input
        type="text"
        v-model="inputValue1"
        @input="logValue1"
        class="w-full border border-gray-300 rounded-lg outline-none py-3 px-2.5 mt-1.5 text-[15px]"
        placeholder="Написать текст..."
      />
    </div>
    <Messages
      title='"Спасибо за звонок в наш колл-центр.'
      content='Мы рады были помочь вам с вашим вопросом. Если у вас возникнут еще какие-либо вопросы или нужна дополнительная помощь, не стесняйтесь обращаться. Пожалуйста, хорошего дня/вечера!"'
    />
    <div class="border-b"></div>
    <div class="flex justify-between items-center p-4">
      <div>
        <label class="flex items-center cursor-pointer">
          <input
            type="checkbox"
            v-model="isChecked"
            class="form-checkbox h-5 w-5 text-[#44C395] border-gray-300 rounded"
          />
          <span class="ml-2 text-black text-[15px]">
            Отправить клиенту СМС-сообщение, с ссылкой на Мобильное приложение - «Zoomrad»
          </span>
        </label>
      </div>

      <div class="flex space-x-2">
        <button
          class="border border-[#F5F6FA] bg-[#F5F6FA] text-[#8294AF] rounded-[8px] font-semibold text-[15px] px-10 py-2 transition duration-200"
          @click="clear"
        >
          Очистить
        </button>
        <button
          class="bg-[#1A99FF] text-white rounded-[8px] font-semibold text-[15px] px-10 py-2 transition duration-200"
          @click="finish"
        >
          Завершить
        </button>
      </div>
    </div>
  </div>
</template>
<script>
import Messages from './Messages.vue'

export default {
  components: {
    Messages // Register the child component
  },
  data() {
    return {
      selectedOption: null,
      selectedOption2: null,
      selectedOption3: null,
      isChecked: false,
      inputValue: 'Абдуллаев Абдулла Абдуллаевич',
      inputValue1: '',
      options: [
        { label: 'Баланс и транзакции', value: 'option1', name: 'options1' },
        { label: 'Жалобы и обратная связь', value: 'option2', name: 'options1' },
        { label: 'Дебетовые карты', value: 'option3', name: 'options1' },
        { label: 'Кредитные продукты', value: 'option4', name: 'options1' },
        { label: 'Инвестиции', value: 'option5', name: 'options1' },
        { label: 'Заявления и документы', value: 'option6', name: 'options1' }
      ], // Default input value
      options2: [
        { label: 'UZCARD DUO', value: 'option2.1', name: 'options2' },
        { label: 'HUMO', value: 'option2.2', name: 'options2' },
        { label: 'VISA', value: 'option2.3', name: 'options2' },
        { label: 'VISA Virtual', value: 'option2.4', name: 'options2' },
        { label: 'UzCard-UnionPay', value: 'option2.5', name: 'options2' },
        { label: 'Банковская карта с индивидуальным', value: 'option2.6', name: 'options2' }
      ],
      options3: [
        { label: 'Информационные запросы', value: 'option3.1', name: 'options3' },
        { label: 'Техническая поддержка', value: 'option3.2', name: 'options3' },
        { label: 'Банковские операции', value: 'option3.3', name: 'options3' },
        { label: 'Статус заявок', value: 'option3.4', name: 'options3' },
        { label: 'Обработка жалоб', value: 'option3.5', name: 'options3' },
        { label: 'Общая информация', value: 'option3.6', name: 'options3' },
        { label: 'Условия продуктов', value: 'option3.6', name: 'options3' }
      ]
    }
  },
  methods: {
    toggleCheckbox() {
      this.isChecked = !this.isChecked // Toggle the checkbox state
    },
    clear() {
      // Clear logic here
      this.isChecked = false // Example logic to reset checkbox
    },
    finish() {
      // Collect all form data into an array of objects
      const formData = [
        {
          name: 'ФИО клиента',
          value: this.inputValue
        },
        {
          name: 'Тема обращения',
          value: this.selectedOption
        },
        {
          name: 'Подтема',
          value: this.selectedOption2
        },
        {
          name: 'Тип обращения',
          value: this.selectedOption3
        },
        {
          name: 'Примечание',
          value: this.inputValue1
        },
        {
          name: 'Отправить_СМС',
          value: this.isChecked
        }
      ]

      // Log the collected form data to the console
      console.log(formData)

      // Perform any further actions (like sending data to an API)
      alert('Форма завершена! Данные отправлены.')
    },
    logValue() {
      console.log(this.inputValue) // Logs the input value to the console
    },
    logValue1() {
      console.log(this.inputValue1) // Logs the input value to the console
    },
    handleRadioChange() {
      // Handle any logic when the radio option changes
      console.log(this.selectedOption3)
    }
  }
}
</script>

<style scoped>
/* Custom checkbox styles */
input[type='checkbox']:checked {
  background-color: #44c395; /* Change to desired color when checked */
  border-color: #44c395; /* Change border color when checked */
}

/* This will apply the styles for unchecked state */
input[type='checkbox'] {
  background-color: white; /* Background color when unchecked */
  border-color: #44c395; /* Border color when unchecked */
}
</style>
