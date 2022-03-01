<template>
  <div :style="designColor">
    <page-header :title="title" :nav="nav" :action="{ to:'#form', name: 'Записаться на группу супервизии' }" />
    <info-block :data="content[0]" position="left" />
    <info-block-img :id="content[1].link" :data="content[1]" position="right" />
    <info-block :id="content[2].link" :data="content[2]" position="left" />
    <info-block :id="content[3].link" :data="content[3]" position="right" />
    <call-to-action :to="{name:'Записаться на группу супервизии', link:'#'}">
      Встречи группы супервизии проходят по вторникам и средам <strong>с 19:00</strong> до <strong>20:30</strong> в онлайн-формате.
    </call-to-action>
    <contact-form />
  </div>
</template>

<script>
import PageHeader from '~/components/PageHeader.vue'
import InfoBlock from '~/components/InfoBlock.vue'
import InfoBlockImg from '~/components/InfoBlockImg.vue'
import CallToAction from '~/components/CallToAction.vue'
import ContactForm from '~/components/Forms/ContactForm.vue'

export default {
  name: 'EducationPage',
  components: {
    PageHeader,
    InfoBlock,
    InfoBlockImg,
    CallToAction,
    ContactForm
  },
  data () {
    return {
      designColor: {
        '--theme-color': 'var(--bg-third)',
        '--theme-text-color': 'var(--main-third)',
        '--theme-block-bg-color': 'var(--bg-third-transparent)'
      },
      title: 'Уже работаю тьютором',
      content: [
        {
          content: [
            'Если вы уже работаете тьютором, вне зависимости от того, нашли вы работу через наш портал или нет, мы будем рады видеть вас на наших группах супервизии.'
          ]
        },
        {
          title: 'Почему участвовать в супервизиях важно?',
          link: 'why',
          content: [
            'Почему участвовать в супервизиях важно и полезно для специалиста? Потому что это - отличная возможность личностного роста и профессионального развития.',
            'Супервизия - форма групповой работы для психологов, тьюторов, педагогов и других специалистов помогающих и социально значимых профессий.',
            'На групповой супервизии участники получают психологическую поддержку и методические рекомендации. Вместе с ведущими обсуждают сложности сопровождения, делятся опытом, находят решения.'
          ]
        },
        {
          title: 'Задачи супервизорской группы',
          link: 'issues',
          content: [
            'Помощь и поддержка в профессиональном росте;',
            'Разрешение затруднений в профессиональной деятельности;',
            'Опыт получения профессиональной супервизии.'
          ]
        },
        {
          title: 'Что даёт супервизия?',
          link: 'supervision',
          content: [
            'Возможность изучить современные методы и значимые детали работы с разными детьми;',
            'Пространство, где можно обсудить с коллегами вопросы из реальной практики и найти выход из сложных ситуаций;',
            'Место для работы на предупреждение эмоционального выгорания.'
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

<style></style>
