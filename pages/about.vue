<template>
  <div :style="designColor">
    <page-header :title="title" :nav="nav" />
    <info-block-img :id="content[0].link" :data="content[0]" />
    <team />
  </div>
</template>

<script>
import PageHeader from '~/components/PageHeader.vue'
import InfoBlockImg from '~/components/InfoBlockImg.vue'
import Team from '~/components/Team.vue'

export default {
  name: 'EducationPage',
  components: {
    PageHeader,
    InfoBlockImg,
    Team
  },
  data () {
    return {
      designColor: {
        '--theme-color': 'var(--bg-second)',
        '--theme-text-color': 'var(--main-pink)',
        '--theme-block-bg-color': 'var(--bg-second-transparent)'
      },
      title: 'О нас',
      content: [
        {
          title: 'Инклюзивный центр «Йом-йом»',
          link: 'selection',
          content: [
            'Центр «Йом-йом» с 2013 года создаёт инклюзивную среду в Петербурге. Мы работаем с детьми - обычными и особыми. Помогаем им стать частью нашего с вами большого мира.',
            'Инклюзивный центр «Йом-йом» растит детей в полной картине мира, где каждому в его уникальности и особенностях есть место.',
            'Мы создали инклюзивную среду у себя в центре и помогаем создать её другим: садам, школам, музеям и библиотекам, кафе и ресторанам, сообществам, родителям и просто людям.',
            'Любой ребенок неразрывно связан с семьей и обществом, в котором он живет. Если окружающая среда будет не готова к принятию, то ребенок навсегда останется в вынужденной изоляции. Мы даём учителям, воспитателям, тьюторам и семьям конкретные инструменты, которые помогают этого не допустить.',
            'Подробнее узнать о нашем центре вы можете на сайте: https://yom-yom.ru/'
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
