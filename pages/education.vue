<template>
  <div :style="designColor">
    <page-header :title="title" :nav="nav" />
    <info-block-img :id="content[0].link" :data="content[0]" />
    <info-block-icons :id="content[1].link" :data="content[1]" position="right" />
    <info-block :id="content[2].link" :data="content[2]" />
  </div>
</template>

<script>
import PageHeader from '~/components/PageHeader.vue'
import InfoBlock from '~/components/InfoBlock.vue'
import InfoBlockImg from '~/components/InfoBlockImg.vue'
import InfoBlockIcons from '~/components/InfoBlockIcons.vue'

export default {
  name: 'EducationPage',
  components: { PageHeader, InfoBlock, InfoBlockImg, InfoBlockIcons },
  data () {
    return {
      designColor: {
        '--theme-color': 'var(--bg-second)',
        '--theme-text-color': 'var(--main-pink)',
        '--theme-block-bg-color': 'var(--bg-second-transparent)'
      },
      title: 'Хочу стать Тьютером',
      content: [
        {
          title: 'Кто такой тьютор для особого ребенка?',
          link: 'who',
          content: [
            'Тьютор для ребёнка с ОВЗ - новая, но уже востребованная профессия среди помогающих специальностей в России. Тьютор помогает особому ребёнку включиться в среду школы или детского сада, поддерживает его, объясняет ему правила поведения и общения, следит чтобы ребенок осваивал учебную программу и выполнял задания. От специалиста требуются эмоциональная поддержка, терпение, внимание и желание помогать.'
          ]
        },
        {
          title: 'Как связаны тьютор и инклюзия?',
          link: 'connection',
          content: [
            'Тьюторское сопровождение детей с особенностями развития - важное звено инклюзивного образования. Благодаря работе тьютора особый ребенок получает образование вместе со сверстниками, может завести друзей и становится частью социума.'
          ]
        },
        {
          title: 'Почему инклюзия так важна?',
          link: 'why',
          content: [
            'Инклюзивное образование появилось в мире в 1960-х годах, но в России до сих пор спорят: работает — не работает, хорошо — плохо. Многие люди сомневаются в том, что у «особых» детей и взрослых могут быть те же потребности, что и у всех остальных — потребность в общении, дружбе, учебе в школе, в занятости и самореализации. Но даже те, кто знаком с проблемой, убеждены: нормотипичные дети, их родители, воспитатели и учителя не готовы находиться рядом с «особыми» детьми в обычных детских садах и школах.',
            'На самом деле это уже не так. Наша практика подтверждает другое. Если «обычные» дети не накручены страхами взрослых, то они легко общаются с «особыми» детьми. Многие взрослые тоже готовы взаимодействовать с «особенными» детьми, иногда нужно только им немного помочь.'
          ]
        }
      ]
    }
  },
  computed: {
    nav () {
      return this.content.map((item) => {
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
