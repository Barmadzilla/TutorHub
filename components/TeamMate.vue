<template>
  <div class="team-mate">
    <div class="placeholder">
      <img
        :src="require('~/assets/images/team/' + data.photo)"
        :alt="`${data.name} - ${data.desc}`"
      >
    </div>
    <div class="info">
      <h3>{{ data.name }}</h3>
      <p class="description">
        {{ data.desc }}
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TeamMate',
  props: {
    data: {
      type: Object,
      require: true,
      default: null
    }
  }
}
</script>

<style scoped>
.placeholder {
  border-radius: 50%;
  overflow: hidden;
  height: 19em;
  width: 19em;
  display: flex;
  justify-content: center;
  align-items: center;
}
img {
  object-fit: fill;
  width: inherit;
}
.team-mate {
  display: grid;
  grid-gap: 2em;
  align-items: center;
  justify-content: center;
  place-items: center;
  width: 25em;
}
.info h3 {
  font-size: 2em;
  margin-bottom: 0.3em;
}
.info p {
  font-size: 1.4em;
  color: var(--text-light);
}
.info {
  text-align: center;
}
@media (max-width: 750px){
  .team-mate {
  width: 60vw;
  }
  .placeholder {
    font-size: 9px;
  }

  .team-mate {
    grid-gap: 5rem;
  }
}
</style>
