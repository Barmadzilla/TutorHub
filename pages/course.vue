<template>
  <div :style="designColor">
    <page-header
      :title="title"
      :nav="nav"
      :action="{ href: 'https://forms.gle/riMGoNpvhfUbAn3D9', name: 'Подать заявку на участие в курсе' }"
    />
    <info-block-img :id="content[0].link" :data="content[0]" />
    <motivation-block :id="content[1].link" :data="content[1]" />
    <call-to-action :to="{ name: 'Подать заявку', link: 'https://forms.gle/riMGoNpvhfUbAn3D9', external: true }">
      Подать заявку на участие в курсе для тьюторов
      <br>
      <strong>«Слышу, вижу и понимаю особого ребёнка»</strong>
    </call-to-action>
    <features-list :id="content[2].link" :data="content[2]" />
    <raised-hands :id="content[3].link" :data="content[3]" />
    <!-- <team-vue title="Ведущие и кураторы" /> -->
    <call-to-action :to="{ name: 'Задать вопрос', link: '/contact' }">
      <h4>Остались вопросы?</h4>
      Воспользуйтесь формой обратной связи
    </call-to-action>
    <testimonials-block :data="content[4]" />
    <contact-form />
  </div>
</template>

<script>
import PageHeader from '~/components/PageHeader.vue'
import InfoBlockImg from '~/components/InfoBlockImg.vue'
import MotivationBlock from '~/components/MotivationBlock.vue'
import CallToAction from '~/components/CallToAction.vue'
// import TeamVue from '~/components/Team.vue'
import FeaturesList from '~/components/FeaturesList.vue'
import RaisedHands from '~/components/RaisedHands.vue'
import TestimonialsBlock from '~/components/TestimonialsBlock.vue'
import ContactForm from '~/components/Forms/ContactForm.vue'

export default {
  name: 'EducationPage',
  components: {
    PageHeader,
    InfoBlockImg,
    MotivationBlock,
    CallToAction,
    // TeamVue,
    FeaturesList,
    RaisedHands,
    TestimonialsBlock,
    ContactForm
  },
  data () {
    return {
      designColor: {
        '--theme-color': 'var(--bg-second)',
        '--theme-text-color': 'var(--main-pink)',
        '--theme-block-bg-color': 'var(--bg-second-transparent)'
      },
      title: 'Курс для тьюторов и специалистов',
      content: [
        {
          title: '«Слышу, вижу и понимаю особого ребёнка»',
          link: 'who',
          content: [
            'Тьютор для ребёнка с ОВЗ - новая, но уже востребованная профессия среди помогающих специальностей в России. Тьютор помогает особому ребёнку включиться в среду школы или детского сада, поддерживает его, объясняет ему правила поведения и общения, следит чтобы ребёнок осваивал учебную программу и выполнял задания. От специалиста требуются эмоциональная поддержка, терпение, внимание и желание помогать.',
            'Тьюторское сопровождение детей с особенностями развития - важное звено инклюзивного образования. Благодаря работе тьютора особый ребёнок получает образование вместе со сверстниками, может завести друзей и становится частью социума. Курс «Слышу, вижу и понимаю особого ребёнка» - часть будущей платформы по поиску тьюторов для семей с особыми детьми. Платформа находится в стадии разработки специалистами центра «Йом-йом».'
          ]
        },
        {
          title: 'Для кого этот курс?',
          link: 'motivation',
          content: [
            {
              icon: 'task.svg',
              description: 'Планируете работать тьютором в ближайшие время'
            },
            {
              icon: 'hierarchy.svg',
              description:
                'Работаете тьютором и хотите стать частью профессионального сообщества'
            },
            {
              icon: 'teamwork.svg',
              description:
                'Готовы стать участником нашей базы тьюторов и получать информацию о вакансиях'
            },
            {
              icon: 'chat.svg',
              description: 'Готовы подключаться к обучению онлайн'
            }
          ]
        },
        {
          title: 'На курсе вы:',
          link: 'on-course-you',
          content: [
            // {
            //   photo: 'feature_1.jpg',
            //   description: 'Готовы стать участником нашей базы тьюторов и получать информацию о вакансиях'
            // },
            {
              photo: 'feature_2.jpg',
              description: 'Познакомитесь с приёмами успешной работы с особыми детьми, как по отдельности, так и в смешанных группах.'
            },
            {
              photo: 'feature_3.jpg',
              description: 'Научитесь налаживать сотрудничество с учителями/воспитателями, администрацией школы/сада.'
            },
            {
              photo: 'feature_4.jpg',
              description: 'Узнаете, как вести себя во время срывов и истерик у детей.'
            },
            {
              photo: 'feature_5.jpg',
              description: 'Поймёте, как не теряться в стрессовых ситуациях.'
            }
          ]
        },
        {
          title: 'Темы курса',
          link: 'themes',
          content: [
            'Адаптация;',
            'Поведение;',
            'Сенсорная интеграция;',
            'Функциональный подход и диагнозы;',
            'Социальные истории;',
            'Визуальные материалы;',
            'Ответы на трудности ребёнка: поощрение, похвала, эффективная коммуникация;',
            'Альтернативная дополнительная коммуникация;',
            'Взаимодействие с родителями;',
            'Роль тьютора, трудности, вызовы, минимизация сопровождения;',
            'Игра, взаимодействие с другими детьми.'
          ]
        },
        {
          title: 'Отзывы участников',
          link: 'testimonials',
          content: [
            {
              name: 'Кристина',
              text: 'На курсе от «Йом-йом» мне удалось получить практические навыки, стать ближе к пониманию поведения особых детей.'
            },
            {
              name: 'Анастасия',
              text: 'После прохождения курса «Йом-йом» сформировалась необходимая база знаний. Преподаватели поддерживали, лекции были информативными, без воды'
            },
            {
              name: 'Екатерина',
              text: 'На курсе «Йом-йом» больше всего мне понравилась тема, где нам рассказали про сенсорные особенности детей. В работе удалось применить новые виды расписаний для детей, упражнения для сенсорной диеты.'
            }
          ]
        }
      ]
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

<style>

</style>
