<template>
  <div class="container" :style="designColor">
    <big-form :title="form.title" :description="form.description" :fields="form.fields" sheet="Parents" />
    <div class="close" @click="$router.back()" />
  </div>
</template>

<script>
import BigForm from '~/components/Forms/BigForm.vue'

export default {
  name: 'ParentForm',
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
        '--theme-color': 'var(--bg-first)',
        '--theme-text-color': 'var(--main-blue)',
        '--theme-block-bg-color': 'var(--bg-first-transparent)'
      },
      form: {
        title: 'Анкета',
        description:
          'Здравствуйте! Заполните, пожалуйста, анкету, которая поможет нам подобрать подходящего Вам тьютора',
        fields: [
          [
            {
              label: '',
              placeholder: 'Имя и Фамилия ребёнка',
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
              placeholder: 'Возраст Ребенка',
              type: 'text',
              name: 'Age',
              value: '',
              required: true
            },
            {
              label: '',
              placeholder: 'Имена родителей',
              type: 'text',
              value: '',
              name: 'parents',
              required: true
            }
          ],
          [
            {
              label:
                'Коротко опишите ребёнка, его особенности и сильные стороны',
              message: 'Коротко опишите ребёнка, его особенности и сильные стороны',
              type: 'text',
              value: '',
              name: 'features',
              required: true
            },
            {
              label: 'В каком учреждении ребёнку понадобится помощь тьютора?',
              message: 'В каком учреждении ребёнку понадобится помощь тьютора?',
              type: 'text',
              value: '',
              name: 'workPlace',
              required: true
            },
            {
              label:
                'Должно ли быть у тьютора профильное образования для трудоустройства у вас?',
              type: 'radio',
              value: '',
              name: 'diploma',
              chose: ['Да', 'Нет'],
              required: true
            },
            {
              label:
                'Сформированы ли у ребёнка навыки самообслуживания? Понадобится ли помощь с походами в туалет и тд?',
              type: 'radio',
              value: '',
              name: 'selfService',
              chose: ['Да', 'Нет'],
              required: true
            },
            {
              label: 'Какая помощь со стороны тьютора потребуется ребёнку?',
              message: 'Какая помощь со стороны тьютора потребуется ребёнку?',
              type: 'text',
              value: '',
              name: 'helpKind',
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
              message: 'Согласие на обработку данных',
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
