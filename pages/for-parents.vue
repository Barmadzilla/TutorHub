<template>
  <div :style="designColor">
    <page-header
      :title="title"
      :nav="nav"
      :action="{ to: '/parent-form', name: 'Заполнить анкету' }"
    />
    <info-block-img :id="content[0].link" :data="content[0]" position="right" />
    <info-block-icons
      :id="content[1].link"
      :data="content[1]"
      position="left"
    />
    <info-block :id="content[2].link" :data="content[2]" position="right" />
    <info-block :id="content[3].link" :data="content[3]" position="left" />
    <!-- <big-form
      :title="form.title"
      :description="form.description"
      :fields="form.fields"
      sheet="Parents"
    /> -->
    <contact-form />
  </div>
</template>

<script>
import PageHeader from '~/components/PageHeader.vue'
import InfoBlock from '~/components/InfoBlock.vue'
import InfoBlockImg from '~/components/InfoBlockImg.vue'
import InfoBlockIcons from '~/components/InfoBlockIcons.vue'
// import BigForm from '~/components/Forms/BigForm.vue'
import ContactForm from '~/components/Forms/ContactForm.vue'

export default {
  name: 'EducationPage',
  components: {
    PageHeader,
    InfoBlock,
    InfoBlockImg,
    InfoBlockIcons,
    // BigForm,
    ContactForm
  },
  data () {
    return {
      designColor: {
        '--theme-color': 'var(--bg-first)',
        '--theme-text-color': 'var(--main-blue)',
        '--theme-block-bg-color': 'var(--bg-first-transparent)'
      },
      title: 'Нам нужен Тьютор',
      content: [
        {
          title: 'Как происходит подбор?',
          link: 'selection',
          content: [
            'Наша платформа содержит базу данных тьюторов, готовых сопровождать детей в школах и детских садах Санкт-петербурга и Ленинградской области.',
            'После того, как мы получим вашу анкету, мы сможем подобрать наиболее подходящего кандидата и организовать ваше знакомство.',
            'В случае удачного подбора, ваши анкеты мы уберём из поиска. Если после знакомства с потенциальным тьютором  по каким-то причинам необходимо будет продолжить поиск, мы постараемся подобрать вам другого подходящего кандидата.'
          ]
        },
        {
          title: 'Как нам найти тьютора?',
          link: 'howFind',
          content: [
            'Чтобы найти тьютора через нашу Платформу, вам нужно заполнить подробную анкету, содержащую вопросы про ребёнка, учреждение и график работы. После заполнения анкеты мы свяжемся с вами и начнём искать для вас подходящего кандидата в тьюторы.'
          ]
        },
        {
          title: 'Сколько это стоит?',
          link: 'howMuch',
          content: [
            'Консультация и подбор подходящего кандидата в тьюторы (в случае удачного подбора) составляет <strong>5000</strong> рублей. Оплата осуществляется через наш сайт, администратор пришлёт вам ссылку на платёжную страницу, когда это потребуется.'
          ]
        },
        {
          title: 'Что ещё вы можете мне предложить?',
          link: 'more',
          content: [
            '<h4>Для вас</h4>',
            '<li>онлайн-встречи ресурсных родительских групп: <a href="https://yom-yom.ru/resource_group">yom-yom.ru/resource_group</a></li><li>К онсультативную поддержку для вас и вашего ребёнка</li><li>Занятия в инклюзивных группах центра "Йом-йом". Подробнее узнать о занятиях: <a href="https://yom-yom.ru/consultative_center">yom-yom.ru/consultative_center</a></li><li>Уроки добра в общеобразовательных  школах и детских садах, которые посещают особые дети. Уроки добра - это цикл занятий, направленных на то, чтобы показать детям, что все мы разные, у каждого есть свои особенности и это абсолютно нормально. Подробнее узнать об уроках добра и договориться об их проведении вы можете, написав нам на почту: <a href="mailto:centr.yomyom@gmail.com">centr.yomyom@gmail.com</a></li>',
            '<h4>Для вашего тьютора</h4>',
            '<li>Групповую супервизию На групповой супервизии участники получают психологическую поддержку и методические рекомендации. Вместе с ведущими обсуждают сложности сопровождения, делятся опытом, находят решения. Участие в группах бесплатное, встречи проходят каждый вторник и среду с 19:00 до 20:30.</li><li>индивидуальную супервизорскую поддержку Специалисты нашего центра будут консультировать его по сложным вопросам, возникающим в ходе сопровождения, оказывать методическую поддержку, помогать разрабатывать дополнительные материалы и в случае необходимости проводить наблюдения в учреждении, которое посещает ваш ребёнок. Стоимость индивидуальной супервизорской поддержки тьютора составляет 5000 рублей/месяц. Подать запрос на поддержку для тьютора от специалистов нашего центра вы можете , написав нам на почту: <a href="mailto:centr.yomyom@gmail.com">centr.yomyom@gmail.com</a></li>'
          ]
        }
      ],
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
  },
  computed: {
    nav () {
      return this.content
        .filter(item => item.link)
        .map((item) => {
          return {
            title: item.title,
            link: item.link
          }
        })
    }
  }
}
</script>

<style></style>
