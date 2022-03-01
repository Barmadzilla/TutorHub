<template>
  <div class="container" :style="designColor">
    <big-form :title="form.title" :description="form.description" :fields="form.fields" sheet="Tutors" />
    <div class="close" @click="$router.back()" />
  </div>
</template>

<script>
import BigForm from '~/components/Forms/BigForm.vue'

export default {
  name: 'TutorForm',
  components: { BigForm },
  layout: 'headless',
  props: {
    open: {
      type: Boolean
    }
  },
  data () {
    return {
      designColor: {
        '--theme-color': 'var(--bg-second)',
        '--theme-text-color': 'var(--main-pink)',
        '--theme-block-bg-color': 'var(--bg-second-transparent)'
      },
      form: {
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
              name: 'email',
              required: true
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
              name: 'education',
              required: true
            },
            {
              label: '',
              placeholder: 'Подходящий график работы:',
              type: 'text',
              value: '',
              name: 'schedule',
              required: true
            }
          ],
          [
            {
              label:
                'Проходили ли вы дополнительное обучение, курсы повышения квалификации и тд? Если да, то какие:',
              message: 'Проходили ли вы дополнительное обучение, курсы повышения квалификации и тд?',
              type: 'text',
              value: '',
              name: 'education',
              required: true
            },
            {
              label:
                'Есть ли у вас предпочтения по районам города, в которых вы готовы работать?',
              message: 'Есть ли у вас предпочтения по районам города, в которых вы готовы работать?',
              type: 'text',
              value: '',
              name: 'preferBlock',
              required: true
            },
            {
              label:
                'Готовы ли вы, в случае отсутствия подходящих вакансий, рассмотреть другие районы?',
              type: 'radio',
              value: '',
              name: 'alternateBlok',
              chose: ['Да', 'Нет'],
              required: true
            },
            {
              label:
                'Есть ли у вас действующий сертификат о вакцинации от Covid-19?',
              type: 'radio',
              value: '',
              name: 'covidCertificate',
              chose: ['Да', 'Нет'],
              required: true
            },
            {
              label:
                'Готовы ли вы помогать ребёнку с самообслуживанием (помощь с походами в туалет, мытьём рук, одеванием и тд)?',
              type: 'radio',
              value: '',
              name: 'selfService',
              chose: ['Да', 'Нет'],
              required: true
            },
            {
              label:
                'Готовы ли вы работать с ребёнком с двигательными особенностями, помогать ему с перемещениями?',
              type: 'radio',
              value: '',
              name: 'cantMove',
              chose: ['Да', 'Нет'],
              required: true
            },
            {
              label:
                'Готовы ли вы на дополнительную занятость с ребёнком (отводить домой, репетиторство по школьным предметам и тд)?',
              type: 'radio',
              value: '',
              name: 'addons',
              chose: ['Да', 'Нет'],
              required: true
            },
            {
              label: 'Ожидаемая заработная плата:',
              placeholder: 'Укажите сумму',
              type: 'text',
              value: '',
              name: 'salary',
              required: true
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
              message: 'Согласен на обработку данных',
              value: [],
              name: 'personalData',
              chose: ['Согласен на обработку данных'],
              required: true
            }
          ]
        ]
      }
    }
  }
}
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
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
.open {
  height: 5rem;
  width: 5rem;
  border-radius: 0.5rem;
  background: var(--theme-color) url('~/assets/icons/chat.svg') no-repeat center /
    60%;
  position: fixed;
  right: 3rem;
  bottom: 3rem;
  box-shadow: 0.2rem 0.2rem 0.8rem rgba(0, 0, 0, 0.23);
  opacity: 0.6;
  cursor: pointer;
  transition: opacity 200ms;
}
.open:hover {
  opacity: 1;
}
@media (max-width: 750px) {
  .container{
    box-sizing: border-box;
    width: 100%;
    height: unset;
  }
}
</style>
