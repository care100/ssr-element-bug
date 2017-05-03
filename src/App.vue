<template>
  <div id="app">
    <header class="header">
      <nav class="inner">
        <router-link to="/" exact>
          <img class="logo" src="~public/logo-48.png" alt="logo">
        </router-link>
        <router-link to="/top">Top</router-link>
        <router-link to="/new">New</router-link>
        <router-link to="/show">Show</router-link>
        <router-link to="/ask">Ask</router-link>
        <router-link to="/job">Jobs</router-link>
        <a class="github" href="https://github.com/vuejs/vue-hackernews-2.0" target="_blank" rel="noopener">
          Built with Vue.js
        </a>
      </nav>

      <el-select size="mini"
                 v-model="form.city">
        <el-option v-for="item in cities"
                   :label="item.label"
                   :key="item.value"
                   :value="item.value"></el-option>
      </el-select>
      <el-form ref="form" :model="form" label-width="95px" :rules="rules"
               @submit.native.prevent="onSubmit">
        <p class="t-title">Test el-form:</p>
        <el-form-item :label="'title'" prop="title">
          <el-input v-model="form.title" name="title"></el-input>
        </el-form-item>
        <el-form-item class="sub-box-message">
          <el-button type="primary" native-type="submit">submit</el-button>
        </el-form-item>
      </el-form>
    </header>
    <transition name="fade" mode="out-in">
      <router-view class="view"></router-view>
    </transition>
  </div>
</template>
<script type="text/javascript">
  export default {
    data () {
      return {
        form: {
          title: '',
          city: 0
        },
        cities: [
          {
            label: 'beijing',
            value: 0
          },
          {
            label: 'shanghai',
            value: 1
          }
        ],
        rules: {
          title: [{
            required: true, message: 'required', trigger: 'blur'
          }]
        }
      }
    },
    methods: {
      onSubmit () {
        console.log('submit')
      }
    }
  }
</script>
<style lang="stylus">
body
  font-family -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen, Ubuntu, Cantarell, "Fira Sans", "Droid Sans", "Helvetica Neue", sans-serif;
  font-size 15px
  background-color lighten(#eceef1, 30%)
  margin 0
  padding-top 55px
  color #34495e
  overflow-y scroll

a
  color #34495e
  text-decoration none

.header
  background-color #ff6600
  position fixed
  z-index 999
  height 55px
  top 0
  left 0
  right 0
  .inner
    max-width 800px
    box-sizing border-box
    margin 0px auto
    padding 15px 5px
  a
    color rgba(255, 255, 255, .8)
    line-height 24px
    transition color .15s ease
    display inline-block
    vertical-align middle
    font-weight 300
    letter-spacing .075em
    margin-right 1.8em
    &:hover
      color #fff
    &.router-link-active
      color #fff
      font-weight 400
    &:nth-child(6)
      margin-right 0
  .github
    color #fff
    font-size .9em
    margin 0
    float right

.logo
  width 24px
  margin-right 10px
  display inline-block
  vertical-align middle

.view
  max-width 800px
  margin 0 auto
  position relative

.fade-enter-active, .fade-leave-active
  transition all .2s ease

.fade-enter, .fade-leave-active
  opacity 0

.el-form
  overflow hidden
  margin-top 30px

.t-title
  margin 0
  float left
  line-height 36px

.el-form-item
  float left

@media (max-width 860px)
  .header .inner
    padding 15px 30px

@media (max-width 600px)
  .header
    .inner
      padding 15px
    a
      margin-right 1em
    .github
      display none
</style>
