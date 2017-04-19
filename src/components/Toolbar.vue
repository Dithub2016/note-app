<template>
  <div id="toolbar">
    <i @click="addOne" class="glyphicon glyphicon-plus"></i>
    <i @click="toggleFavorite"
       class="glyphicon glyphicon-star"
       :class="{starred: activeNote.favorite}"
    ></i>
    <i @click="deleteNote" class="glyphicon glyphicon-remove"></i>
  </div>
</template>

<script>
export default {
  computed: {
      activeNote () {
          return this.$store.getters.activeNote
      }
  },
    methods: {
      addOne () {
          // 通过 dispatch 分发到 actions 中的 addNote
          this.$store.dispatch('addNote')
      },
      toggleFavorite () {
        this.$store.dispatch('toggleFavorite')
      },
      deleteNote () {
        this.$store.dispatch('deleteNote')
      }
    }
}
</script>

<style lang="sass">
#toolbar
  float: left
  width: 80px
  height: 100%
  background-color: #30414d
  color: #767676
  padding: 35px 25px 25px 25px

  i
    font-size: 30px
    margin-bottom: 35px
    cursor: pointer
    opacity: .8
    transition: opoacity .5s ease

    &:hover
      opacity: 1

.starred
  color: #f7ae4f
</style>
