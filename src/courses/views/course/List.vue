<template>
  <div class="content">
  <table class="table">
    <thead>
      <tr>
        <th>课程名称</th>
        <th>任课老师</th>
        <th>开始时间</th>
        <th>结束时间</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="course in courseList">
        <td>{{course.courseName}}</td>
        <td>{{course.teacher}}</td>
        <td>{{course.startTime}}</td>
        <td>{{course.endTime}}</td>
      </tr>
    </tbody>
  </table>
    <a class="btn" v-link="{ path: '/course/create' }">新建课程</a>
  </div>
</template>
<script>
  import { fetchCourses } from '../../actions/CourseActions';
  export default {
    vuex: {
      getters: {
        courseList: state => state.course.courseList,
      },
      actions: {
        fetchCourses,
      },
    },
    ready() {
      console.log('fetch course');
      this.fetchCourses();
    }
  };
</script>
