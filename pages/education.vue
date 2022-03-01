<template>
  <div :style="designColor">
    <page-header
      :title="title"
      :nav="nav"
      :action="{ to: '/tutor-form', name: 'Заполнить анкету' }"
    />
    <info-block-img :id="content[0].link" :data="content[0]" />
    <info-block-icons
      :id="content[1].link"
      :data="content[1]"
      position="right"
    />
    <!-- <info-block :id="content[2].link" :data="content[2]" /> -->
    <!-- <accordion-block :id="content[3]" :data="content[3]" /> -->
    <road-map :id="content[4].link" :data="content[4]" />
    <!-- <big-form :title="form.title" :description="form.description" :fields="form.fields" sheet="Tutors" /> -->
    <contact-form />
  </div>
</template>

<script>
import PageHeader from '~/components/PageHeader.vue'
// import InfoBlock from '~/components/InfoBlock.vue'
import InfoBlockImg from '~/components/InfoBlockImg.vue'
import InfoBlockIcons from '~/components/InfoBlockIcons.vue'
import RoadMap from '~/components/RoadMap.vue'
// import AccordionBlock from '~/components/AccordionBlock.vue'
// import BigForm from '~/components/Forms/BigForm.vue'
import ContactForm from '~/components/Forms/ContactForm.vue'

export default {
  name: 'EducationPage',
  components: {
    PageHeader,
    // InfoBlock,
    InfoBlockImg,
    InfoBlockIcons,
    RoadMap,
    // AccordionBlock,
    // BigForm,
    ContactForm
  },
  data () {
    return {
      designColor: {
        '--theme-color': 'var(--bg-second)',
        '--theme-text-color': 'var(--main-pink)',
        '--theme-block-bg-color': 'var(--bg-second-transparent)'
      },
      title: 'Хочу стать Тьютором',
      content: [
        {
          title: 'Кто такой тьютор для особого ребёнка?',
          link: 'who',
          content: [
            'Тьютор для ребёнка с ОВЗ - новая, но уже востребованная профессия среди помогающих специальностей в России. Тьютор помогает особому ребёнку включиться в среду школы или детского сада, поддерживает его, объясняет ему правила поведения и общения, следит чтобы ребенок осваивал учебную программу и выполнял задания. От специалиста требуются эмоциональная поддержка, терпение, внимание и желание помогать.'
          ]
        },
        {
          title: 'Как связаны тьютор и инклюзия?',
          link: 'connection',
          content: [
            'Тьюторское сопровождение детей с особенностями развития - важное звено инклюзивного образования. Благодаря работе тьютора особый ребёнок получает образование вместе со сверстниками, может завести друзей и становится частью социума.'
          ]
        },
        {
          title: 'Почему инклюзия так важна?',
          link: 'why',
          content: [
            'Инклюзивное образование появилось в мире в 1960-х годах, но в России до сих пор спорят: работает — не работает, хорошо — плохо. Многие люди сомневаются в том, что у «особых» детей и взрослых могут быть те же потребности, что и у всех остальных — потребность в общении, дружбе, учебе в школе, в занятости и самореализации. Но даже те, кто знаком с проблемой, убеждены: нормотипичные дети, их родители, воспитатели и учителя не готовы находиться рядом с «особыми» детьми в обычных детских садах и школах.',
            'На самом деле это уже не так. Наша практика подтверждает другое. Если «обычные» дети не накручены страхами взрослых, то они легко общаются с «особыми» детьми. Многие взрослые тоже готовы взаимодействовать с «особенными» детьми, иногда нужно только им немного помочь.'
          ]
        },
        {
          title: 'Хотим поделиться с вами некоторыми тонкостями включения:',
          content: [
            {
              title: 'Когда никто не исключен',
              desc: 'Когда никто не исключен, все дети, независимо от способностей и особенностей, могут ладить между собой',
              img: 'photo_01.jpg'
            },
            {
              title: 'Дошкольный возраст',
              desc: 'Дошкольный возраст – лучшее время для восприятия детьми особенностей других; в этом возрасте стираются границы в общении детей друг с другом.',
              img: 'photo_02.jpg'
            },
            {
              title: 'Самые результативные занятия ',
              desc: 'Самые результативные занятия с лучшими специалистами не могут заменить детям полноценного общения со сверстниками, нормальная детская жизнь терапевтична сама по себе',
              img: 'photo_03.jpg'
            },
            {
              title: 'Общение и игра',
              desc: 'Общение и игра с «особыми» детьми помогают «обычным» детям стать добрее, улучшить собственные навыки общения и игры, научиться заботиться о других людях.',
              img: 'photo_04.jpg'
            },
            {
              title: 'Включение особых детей',
              desc: 'Включение особых детей - это ситуация выигрыша обеих сторон, стратегия win-win («победа-победа»), нет каких-либо жертв или потерь со стороны «обычных» детей, только приобретения.',
              img: 'photo_05.jpg'
            },
            {
              title: 'Инклюзивные подходы',
              desc: 'Инклюзивные подходы помогают нормализовать не только жизнь детей, но и родителей. Счастливые родители - путь к счастливым детям.',
              img: 'photo_06.jpg'
            },
            {
              title: 'Трудные вопросы и ситуации',
              desc: 'Трудные вопросы и ситуации случаются у всех родителей, обычные дети имеют характеры и особенности, сотрудники могут болеть и уставать. А инклюзивная среда дружественна, поддерживает и питает всех, особых и обычных, детей и взрослых, родителей и сотрудников.',
              img: 'photo_07.jpg'
            },
            {
              title: 'Методики и практики инклюзии',
              desc: 'Методики и практики инклюзии применимы в обычных группах детских садов и в школьных классах.',
              img: 'photo_08.jpg'
            }
          ]
        },
        {
          link: 'roadmap',
          title: 'Что нужно, чтобы стать тьютором?',
          content: [
            // 'Зайти на портал ТьюторХаб',
            'Заполнить анкету',
            'Пройти наш курс в групповом или индивидуальном порядке',
            'Познакомиться с ребёнком, семьёй, учреждением',
            'Начать сопровождать ребёнка в учреждении',
            'Посещать группы супервизии для тьюторов'
          ]
        }
      ],
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
