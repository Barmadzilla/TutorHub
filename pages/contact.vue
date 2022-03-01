<template>
  <div class="container">
    <div class="close" @click="$router.back()" />
    <div v-show="!showModal" class="open" @click="showModal = true" />
    <form v-show="showModal">
      <div v-if="!submitted && !loading" class="fields">
        <h2>Есть вопросы? Напишите нам </h2>
        <input-text v-model="fields[0].value" :data="fields[0]" />
        <input-text v-model="fields[1].value" :data="fields[1]" />
        <input-text v-model="fields[2].value" :data="fields[2]" />
        <div>
          <p>{{ fields[3].label }}</p>
          <div class="radio-container">
            <div
              v-for="(item, m) in fields[3].chose"
              :key="m"
              class="radio"
              :class="{ active: item === fields[3].value }"
            >
              <input
                :id="fields[3].name + m"
                v-model="fields[3].value"
                :value="item"
                :name="fields[3].name"
                :type="fields[3].type"
                :placeholder="item.placeholder"
              >
              <label :for="fields[3].name + m">{{ item }}</label>
            </div>
          </div>
        </div>
        <textarea
          :id="fields[4].name"
          v-model="fields[4].value"
          :type="fields[4].type"
          :placeholder="fields[4].placeholder"
        />
        <button class="btn" :disabled="!validate" @click.prevent="submitForm">
          Отправить вопрос
        </button>
        <!-- <pre>{{ fields }}</pre> -->
        <!-- <pre>{{ message }}</pre> -->
      </div>
      <div v-else>
        <div v-if="error">
          <p>К сожалению что-то пошло не так:(</p>
        </div>
        <div v-else>
          <div v-if="loading">
            <p>Отправляем...</p>
          </div>
          <div v-else>
            <p>Ваш вопрос отправлен</p>
          </div>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
import InputText from '~/components/Forms/Fields/InputText.vue'

export default {
  name: 'ContactPage',
  components: { InputText },
  layout: 'headless',
  props: {
    open: {
      type: Boolean
    }
  },
  data () {
    return {
      showModal: true,
      submitted: false,
      loading: false,
      error: false,
      fields: [
        {
          name: 'name',
          placeholder: 'Имя',
          value: '',
          type: 'text',
          required: true
        },
        {
          name: 'email',
          placeholder: 'E-mail',
          value: '',
          type: 'text',
          required: true
        },
        {
          name: 'Tel',
          placeholder: 'Телефон',
          value: '',
          type: 'text'
        },
        {
          name: 'source',
          label: 'Kак удобно получить ответ?',
          chose: ['Email', 'Whatsapp'],
          value: 'Email',
          type: 'radio',
          required: true
        },
        {
          name: 'source',
          placeholder: 'Вопрос...',
          value: '',
          type: 'textarea',
          required: true
        }
      ]
    }
  },
  computed: {
    steps () {
      return this.fields.length
    },
    allValues () {
      return this.fields.flat().map(item => item.value)
    },
    validate () {
      return this.fields.flat().filter(item => item?.required).every(this.fieldValueIs)
    },
    message () {
      return `\n${this.fields[4].value}\n\nПрошу ответить мне на ${this.fields[3].value}.\nНомер моего телефона: ${this.fields[2].value} \nМой Email: ${this.fields[1].value}`
    }
  },
  methods: {
    fieldValueIs (element) {
      if (typeof element.value === 'object') {
        return element.value[0]
      } else {
        return element.value
      }
    },
    openContactModal () {
      this.showModal = true
    },
    async submitForm () {
      this.loading = true
      const result = await this.$axios.post('https://api.tutorhub.ru/mail', { name: this.fields[0].value, message: this.message })
      if (await result && result.data === 'OK') {
        this.submitted = true
        this.loading = false
      } else {
        this.error = true
      }
      setTimeout(() => {
        this.showModal = false
        this.submitted = false
        this.$router.back()
      }, 1500)
    }
  }
}
</script>

<style scoped>
.container{
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
form {
  padding: 3rem;
  border-radius: 2rem;
  background: white;
  right: 3rem;
  bottom: 3rem;
  width: 45rem;
  z-index: 1000;
}
.fields{
  display: grid;
  grid-gap: 2rem;
}
h2 {
  color: var(--theme-text-color);
  padding: 0;
  margin-bottom: 2rem;
}
.page {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 3rem;
  padding-bottom: 2rem;
}

form {
  border-radius: 2rem;
  padding: 5rem;
  border: solid 0.3em var(--theme-color);
}
input::placeholder {
  color: var(--color-placeholder);
}
input:not(input[type='checkbox']),
input:not(input[type='radio']),
textarea {
  background: var(--color-bg-input);
  border: 1px solid var(--color-border-input);
  font-size: 1.6rem;
  padding: 1.7rem 2rem 1.6rem;
  border-radius: 0.6rem;
  line-height: 1.4;
  width: 100%;
  box-sizing: border-box;
}
.fields .full {
  grid-column: span 2;
}

textarea {
  height: 10rem;
}
.radio input[type='radio'],
.checkbox input[type='checkbox'] {
  appearance: none;
  padding: 0;
  margin: 0;
  border-radius: 50%;
  --size: 3rem;
  height: var(--size);
  width: var(--size);
  margin-right: 1rem;
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  transition: all 200ms;
}
.radio.active label {
  color: var(--theme-text-color);
}
.radio.active input[type='radio']::before,
.checkbox input[type='checkbox']::before {
  content: '';
  position: absolute;
  --size: 2rem;
  height: var(--size);
  width: var(--size);
  background: var(--theme-text-color);
  border-radius: 50%;
  z-index: 1;
}

.checkbox input[type='checkbox'] {
  border-radius: 0.3rem;
}
.checkbox input[type='checkbox']::before {
  height: 20%;
  top: 0.3em;
  background: var(--color-border-input);
  border-radius: 0.2rem;
  align-self: flex-start;
  transition: all 150ms;
}
.checkbox.active input[type='checkbox']::before {
  background: var(--theme-text-color);
  align-self: flex-end;
  bottom: 0.2em;
  height: 30%;
  top: calc(100% - 30% - 0.3em);
}
nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-top: 3.5rem;
  border-top: 0.2rem solid var(--theme-color);
  margin-top: 2rem;
  transition: all 150ms;
}
nav.first {
  justify-content: flex-end;
}
label {
  font-size: 1.4em;
  padding-bottom: 1rem;
  display: inline-block;
}
.radio-container {
  display: flex;
  gap: 3em;
}
.radio,
.checkbox {
  display: flex;
  align-items: center;
}
.radio label,
.checkbox label {
  font-size: 1.6rem;
  line-height: 1;
  color: gray;
  margin: 0;
  padding: 0;
}
.page-numbers {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 20rem;
  padding: 2rem 0;
  position: relative;
  z-index: 2;
}
.page-numbers button {
  border-radius: 50%;
  padding: 0;
  margin: 0;
  --size: 6rem;
  width: var(--size);
  height: var(--size);
  font-size: 2.5rem;
  font-size: bold;
  text-align: center;
  padding: 0.3rem 0 0 0.1rem;
  border-color: var(--theme-color);
  color: var(--theme-color);
  background: white;
}
.page-numbers button.active {
  border-color: var(--theme-text-color);
  color: var(--theme-text-color);
}
.page-numbers button:hover {
  color: var(--theme-text-color);
}
.page-numbers::before {
  content: '';
  height: 0.2rem;
  background: var(--theme-color);
  width: 100%;
  position: absolute;
  z-index: -1;
  border-radius: 1em;
}
.toFill{
  font-size: 1.2;
  padding: 2rem;
  border-radius: .5rem;
  background: rgba(255, 0, 0, 0.23);
}
ul{
  margin: 1.5rem 0 0 0;
}
.toFill li{
  font-size: 1.4rem;
  margin-bottom: .7rem;
}
.toFill li:last-child{
  margin: 0;
}
.agreement{
  margin-bottom: 2rem;
}
.agreement p{
  font-size: 1.3em;
}
.close {
  position: absolute;
  top: 2rem;
  right: 2rem;
  height: 2rem;
  width: 2rem;
  z-index: 1;
  display: flex;
  justify-content: center;
  align-items: center;
  --thin: 0.3rem;
  cursor: pointer;
}
.close::after,
.close::before {
  background: grey;
  z-index: 2;
  position: absolute;
  border-radius: 0.2rem;
  transform: rotate(45deg);
}
.close::after {
  content: '';
  width: 100%;
  height: var(--thin);
}
.close::before {
  content: '';
  height: 100%;
  width: var(--thin);
}
.open{
  height: 5rem;
  width: 5rem;
  border-radius: .5rem;
  background: var(--theme-color) url('~/assets/icons/chat.svg') no-repeat center / 60%;
  position: fixed;
  right: 3rem;
  bottom: 3rem;
  box-shadow: 0.2rem 0.2rem 0.8rem rgba(0, 0, 0, 0.23);
  opacity: .6;
  cursor: pointer;
  transition: opacity 200ms;
}
.open:hover {
  opacity: 1;
}
@media (max-width: 750px){
  container {
    max-width: 70rem;
    width: 100vw;
    height: 100vh;
    border-radius: 0;
    box-sizing: border-box;
    top: 0;
    left: 0;
    display: flex;
    align-items: center;
  }
}
</style>
