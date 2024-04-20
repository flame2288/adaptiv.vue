<script setup>
import { ref } from 'vue';



const name = ref('');
const question = ref('');
const phone = ref('');
const email = ref('');
const success = ref(false)

async function onSubmit (){
  console.log(name.value, question.value, phone.value, email.value)
  const botToken = '7046223616:AAEX7tRI4SNX2pGR3cUxG1JDUvA3fG6HYXc';
  const chatID = '-1002063442880';
  const text = `Новое сообщение: %0A%0A` + 
              `Вопрос: ${question.value}%0A` +
              `Имя: ${name.value}%0A` + 
              `Телефон: ${phone.value}%0A` + 
              `Эл. почта: ${email.value}%0A`;
              await fetch(`https://api.telegram.org/bot${botToken}/sendMessage?chat_id=${chatID}&text=${text}`)
              .then((responce)=>{
                if (responce.status === 200) {
                success.value = true; 
                }
                
              })
              .catch((error)=>{
                success.value = false;
                console.log(error)
              })
              const massage = success.value ? 'Отправлено!' :'Произошла ошибка, попробуйте позже!';
              alert(massage);
              question.value = '';
              name.value = '';
              phone.value = '';
              email.value = '';
    
}
// https://api.telegram.org/bot<Bot_token>/sendMessage?chat_id=<chat_id>&text=Привет%20мир
</script>

<template>    
<section class="feelback">
          <div class="container">
            <div class="row  justify-content-center">
              <div class="col-xl-6">
                <div class="feelback__text">
                  <h2>Остались вопросы?</h2>
                  <p>Свяжитесь с нами!</p>
                </div>
              </div>
              <div class="col-12 col-lg-9 col-xl-6">
                <form class="form" method="post" @submit.prevent="onSubmit">
                  <label class="mb-3">
                  <textarea placeholder="Введите ваш вопрос" required title="Введите ваш вопрос"
                  v-model="question"></textarea>
                </label>
                <div class="form__group">
                <label class="form__textatea-label">
                  <input type="text" placeholder="Ваше имя" required title="Введите ваше имя" maxlength="15"
                  v-model="name">
                </label>
                <label>
                  <input type="tel" placeholder="+7(___)___-____" pattern="[0-9]{11}" maxlength="11"
                   required  title="Введите ваш номер телефона" v-model="phone">
                </label>
                <label>
                  <input type="email" placeholder="Электронная почта"
                  required title="Введите вашу электронную почту" maxlength="255" v-model="email">
                </label>
              </div>
                <button class="button-primary mb-0 mb-lg-3" type="submit">Отправить</button>
                </form>
              </div>
            </div>
          </div>
        </section>

</template> 

<style scoped>

</style>