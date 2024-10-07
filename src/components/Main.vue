<template>
  <div class="mx-8">
    <Calling />

    <Messages
      title='"Добрый день и добро пожаловать в кОлл-центр АК «Aloqabank»!"'
      content='Мы рады видеть вас и готовы оказать качественную помощь в решении всех ваших финансовых
      вопросов. Чем могу быть полезен сегодня? Могу я узнать ваше полное имя, пожалуйста? Это
      поможет нам обеспечить более персонализированное обслуживание и быстрее решить ваш вопрос."'
    />
    <InfoClients />

    <Tables @send-data="handleData" />
  </div>
</template>

<script>
import Messages from './Messages.vue'
import Calling from './Calling.vue'
import InfoClients from './InfoClients.vue'
import Tables from './Tables.vue'
export default {
  components: {
    Messages,
    Calling,
    InfoClients,
    Tables
  },
  data() {
    return {
      childData: '' // State to hold data from child
    }
  },
  methods: {
    handleData(data) {
      this.childData = data // Update state with data received from child
    }
  }
}
</script>

<style scoped>
/* header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
} */
</style>
