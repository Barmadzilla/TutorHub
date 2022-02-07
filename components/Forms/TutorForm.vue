<template>
  <content-section id="form">
    <form>
      <h2>{{ title }}</h2>
      <p>{{ description }}</p>
      <div class="page-numbers">
        <button v-for="(page, i) in fields" :key="i" :class="{ active: i === step }" @click.prevent="step = i">
          {{ i + 1 }}
        </button>
      </div>
      <div class="fields">
        <div v-for="(page, i) in fields" :key="i">
          <div v-if="step === i" class="page">
            <div v-for="(field, n) in page" :key="n" :class="{ full: field.span }">
              <label v-if="field.label" :for="field.name">{{ field.label }}</label>
              <input
                v-if="textFields(field.type)"
                :id="field.name"
                v-model="field.value"
                :type="field.type"
                :placeholder="field.placeholder"
              >
              <textarea
                v-if="field.type === 'textarea'"
                :id="field.name"
                v-model="field.value"
                :type="field.type"
                :placeholder="field.placeholder"
              />
              <div v-if="field.type === 'radio'" class="radio-container">
                <div v-for="item, m in field.chose" :key="m" class="radio" :class="{ active: item === field.value }">
                  <input
                    :id="field.name + m"
                    v-model="field.value"
                    :value="item"
                    :name="field.name"
                    :type="field.type"
                    :placeholder="item.placeholder"
                  >
                  <label :for="field.name + m">{{ item }}</label>
                </div>
              </div>
              <div v-if="field.type ==='checkbox'" class="radio-container">
                <div v-for="item, m in field.chose" :key="m" class="checkbox" :class="{ active: field.value.find(a => a === item) }">
                  <input
                    :id="field.name + m"
                    v-model="field.value"
                    :value="item"
                    :name="item"
                    :type="field.type"
                    :placeholder="item.placeholder"
                  >
                  <label :for="field.name + m">{{ item }}</label>
                </div>
              </div>
            </div>
          </div>
        </div>
        <nav :class="{first: step === 0}">
          <button v-if="step > 0" href="#form" class="btn" @click.prevent="step --">
            Назад
          </button>
          <button
            v-if="step < steps - 1"
            href="#form"
            class="btn"
            @click.prevent="step ++"
          >
            Вперед
          </button>
          <button v-else class="btn" @click.prevent="">
            Отправить данные
          </button>
        </nav>
      </div>
      <!-- <pre>
          {{ fields[2] }}
      </pre> -->
    </form>
  </content-section>
</template>

<script>
import ContentSection from '../ContentSection.vue'
export default {
  name: 'TutorForm',
  components: { ContentSection },
  data () {
    return {
      step: 0,
      title: 'Анкета',
      description:
        'Здравствуйте! Заполните, пожалуйста, анкету, которая поможет нам подобрать подходящую вам вакансию.',
      fields: [
        [
          {
            label: '',
            placeholder: 'Имя Фамилия',
            type: 'text',
            name: 'FullName',
            value: '',
            required: true
          },
          {
            placeholder: 'Ваш телефон',
            type: 'text',
            name: 'phone',
            value: '',
            required: true
          },
          {
            label: '',
            placeholder: 'E-mail для связи',
            type: 'email',
            value: '',
            name: 'email'
          },
          {
            label: '',
            placeholder: 'Ваш возраст',
            type: 'text',
            name: 'Age',
            value: '',
            required: true
          },
          {
            label: '',
            placeholder: 'Какое у вас образование?',
            type: 'text',
            value: '',
            name: 'education'
          },
          {
            label: '',
            placeholder: 'Подходящий график работы:',
            type: 'text',
            value: '',
            name: 'schedule'
          }
        ],
        [
          {
            label: 'Проходили ли вы дополнительное обучение, курсы повышения квалификации и тд? Если да, то какие:',
            type: 'text',
            value: '',
            name: 'education'
          },
          {
            label: 'Есть ли у вас предпочтения по районам города, в которых вы готовы работать?',
            type: 'text',
            value: '',
            name: 'preferBlock'
          },
          {
            label: 'Готовы ли вы, в случае отсутствия подходящих вакансий, рассмотреть другие районы?',
            type: 'radio',
            value: '',
            name: 'alternateBlok',
            chose: ['Да', 'Нет']
          },
          {
            label: 'Есть ли у вас действующий сертификат о вакцинации от Covid-19?',
            type: 'radio',
            value: '',
            name: 'covidCertificate',
            chose: ['Да', 'Нет']
          },
          {
            label: 'Готовы ли вы помогать ребёнку с самообслуживанием (помощь с походами в туалет, мытьём рук, одеванием и тд)?',
            type: 'radio',
            value: '',
            name: 'selfService',
            chose: ['Да', 'Нет']
          },
          {
            label: 'Готовы ли вы работать с ребёнком с двигательными особенностями, помогать ему с перемещениями?',
            type: 'radio',
            value: '',
            name: 'cantMove',
            chose: ['Да', 'Нет']
          },
          {
            label: 'Готовы ли вы на дополнительную занятость с ребёнком (отводить домой, репетиторство по школьным предметам и тд)?',
            type: 'radio',
            value: '',
            name: 'addons',
            chose: ['Да', 'Нет']
          },
          {
            label: 'Ожидаемая заработная плата:',
            placeholder: 'Укажите сумму',
            type: 'text',
            value: '',
            name: 'salary'
          }
        ],
        [
          {
            label: 'Любые комментарии, вопросы:',
            type: 'textarea',
            value: '',
            name: 'commentaries',
            span: true
          },
          {
            type: 'checkbox',
            value: [],
            name: 'personalData',
            chose: ['Согласен на обработку данных']
          }
        ]
      ]
    }
  },
  computed: {
    steps () {
      return this.fields.length
    }
  },
  methods: {
    textFields (type) {
      return type === 'text' || type === 'tel' || type === 'email'
    }
  }
}
</script>

<style scoped>
h2 {
  color: var(--theme-text-color);
}
.fields{
  padding-top: 2em;
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
input:not(input[type=checkbox]),
input:not(input[type=radio]),
textarea {
  background: var(--color-bg-input);
  border: 1px solid var(--color-border-input);
  font-size: 1.6rem;
  padding: 1.7rem 2rem 1.6rem;
  border-radius: 0.6rem;
  line-height: 1;
  width: 100%;
  box-sizing: border-box;
}
.fields .full{
  grid-column: span 2;
}

textarea{
  height: 10rem;
}
.radio input[type='radio'],
.checkbox input[type=checkbox]{
  appearance: none;
  padding: 0;
  margin: 0;
  border-radius: 50%;
  --size:3rem;
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
.radio.active label{
  color: var(--theme-text-color);
}
.radio.active input[type='radio']::before,

.checkbox input[type='checkbox']::before  {
  content: '';
  position: absolute;
  --size:2rem;
  height: var(--size);
  width: var(--size);
  background: var(--theme-text-color);
  border-radius: 50%;
  z-index: 1;
}

.checkbox input[type=checkbox]{
    border-radius: .3rem;
}
.checkbox input[type='checkbox']::before {
  height: 20%;
  top: .3em;
  background: var(--color-border-input);
  border-radius: .2rem;
  align-self: flex-start;
  transition: all 150ms;
}
.checkbox.active input[type='checkbox']::before {
  background: var(--theme-text-color);
  align-self: flex-end;
  bottom: .2em;
  height: 30%;
  top: calc(100% - 30% - .3em);
}
nav{
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-top: 3.5rem;
  border-top: .2rem solid var(--theme-color);
  margin-top: 2rem;
  transition: all 150ms;
}
nav.first{
  justify-content: flex-end;
}
label{
  font-size: 1.4em;
  padding-bottom: 1rem;
  display: inline-block;
}
.radio-container{
  display: flex;
  gap: 3em;
}
.radio, .checkbox{
  display: flex;
  align-items: center;
}
.radio label,.checkbox label{
  font-size: 1.6rem;
  line-height: 1;
  color: gray;
  margin: 0;
  padding: 0;
}
.page-numbers{
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 20rem;
  padding: 2rem 0;
  position: relative;
  z-index: 2;
}
.page-numbers button{
  border-radius: 50%;
  padding: 0;
  margin: 0;
  --size: 6rem;
  width: var(--size);
  height: var(--size);
  font-size: 2.5rem;
  font-size: bold;
  text-align: center;
  padding: .3rem 0 0 .1rem;
  border-color: var(--theme-color);
  color: var(--theme-color);
  background: white;
}
.page-numbers button.active{
  border-color: var(--theme-text-color);
  color: var(--theme-text-color);
}
.page-numbers button:hover{
  color: var(--theme-text-color);
}
.page-numbers::before{
  content: '';
  height: .2rem;
  background: var(--theme-color);
  width: 100%;
  position: absolute;
  z-index: -1;
  border-radius: 1em;
}
</style>
