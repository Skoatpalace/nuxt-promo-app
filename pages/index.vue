<template>
  <div>
    <hero />
    <section class="section">
      <div class="container">
        <h1 class="title">Featured Courses</h1>
        <div class="columns">
          <div v-for="course in courses" 
              :key="course._id" 
              class="column is-one-quarter">
            <!-- CARD-ITEM -->
            <courseCard :course="course"/>
            <!-- CARD-ITEM-END -->
          </div>
        </div>
      </div>
    </section>
    <section class="section">
      <div class="container">
        <h1 class="title">Featured Articles</h1>
        <div class="columns">
          <div class="column is-one-quarter">
            <!-- CARD-ITEM -->
            <blogCard />
            <!-- CARD-ITEM-END -->
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import Hero from '~/components/shared/Hero'
import BlogCard from '~/components/BlogCard'
import CourseCard from '~/components/CourseCard'
import { mapState } from 'vuex'
export default {
  components: {
    Hero,
    BlogCard,
    CourseCard
  },
  computed: {
    ...mapState({
      courses: state => state.course.items
    })
  },
  async fetch({ store }) {
    await store.dispatch('course/fetchCourses')
  }
}
</script>

<style scoped lang="scss">
  // Home page
  .links {
    padding-top: 15px;
  }
</style>    