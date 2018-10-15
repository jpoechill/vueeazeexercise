<template>
  <div id="app"> 
    <header>
      <div class="container header d-none d-md-block">
        <div class="row">
          <div class="col-md-9 logo-type">
            <a href="/">Giphietrends</a>
          </div>
          <div class="col-md-3 search-type">
            <input type="text" size="30" v-model="searchQuery" v-on:keyup.enter="handleSearch()" placeholder="Search people, places, things">
          </div>
        </div>
      </div>
      <div class="container header d-md-none">
        <div class="row">
          <div class="col-sm-12">
            <div class="logo-type" style="display: inline-block;">
              <a href="/">G//</a>
            </div>
            <div class="search-type search-type_sml" style="display: inline-block;">
              <input type="text" size="30" v-model="searchQuery" v-on:keyup.enter="handleSearch()" placeholder="Search people, places, things">
            </div>
          </div>
        </div>
      </div>
    </header>
    <section>
      <div class="container">
        <div class="row">
          <div class="col-md-12 trending-container">
            <b>Trending</b>
          </div>
        </div>
        <div class="row">
          <div class="col-md-12">
            <transition-group appear name="fade">
              <div v-for="(image, index) in list" v-bind:style="{ 'z-index': image.zIndex, width: image.images.fixed_height_still.width + 'px', height: image.images.fixed_height_still.height + 'px'}" :key="image.id" v-on:mouseover="itemHover(index, image.images.fixed_height_still.url, image.images.fixed_height.url)" style="position: relative" v-on:mouseout="itemHoverOut(index)" class="image-container box" >
                <div v-if="image.infoTextVis" v-bind:style="{ width: image.images.fixed_height_still.width + 'px', height: image.images.fixed_height_still.height + 'px'}" style="color: #FFF; font-size: 12px; padding: 16px; position: absolute; overflow: hidden; z-index: 1000; line-height: 15px;">
                  {{ image.title }} <br>
                  uploaded 10 days ago <br>
                </div>
                <div class="linear-gradient" v-bind:style="{ width: image.images.fixed_height_still.width + 'px', height: image.images.fixed_height_still.height + 'px'}" style="bottom: 0px; position: absolute;">
                </div>
                <div>
                  <img :src="image.images.currUrl" >
                </div>
              </div>
            </transition-group>
          </div>
        </div>
      </div>
    </section>
    <footer>
      <div class="container footer">
        <div class="row">
          <div class="col-md-12">You've reached the bottom.</div>
        </div>
      </div>
    </footer>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'app',
  components: {
    HelloWorld
  }
}
</script>

<style lang="scss">

$black: #111;

html, body {
  font-family: "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
  background-color: $black;
}
*, *:before, *:after {
  box-sizing: border-box;
  margin: 0;
}

a, a:visited {
  color: #FFF;
}

a:hover {
  color: #FFF;
  text-decoration: none;
}

header {
  background-color: #111;
  width: 100%;
}

.header {
  color: #FFF;
  background-color: $black;
  font-size: 48px;
  height: 74px;
  width: 100%;

  .row {
    width: 100%;
    background-color: $black;
  }
}

.logo-type {
  margin-top: 10px;
  font-family: 'Fugaz One'
}

input[type="text"] {
  padding: 4px;
  size: 100;
  border-style: solid;
  color: #DDD;
  -webkit-appearance: none;
  background-color : $black; 
}

input:focus {
  outline: none;
}

.search-type {
  padding-top: 30px;
  font-size: 14px;
}

.search-type_sml {
  margin-left: 30px;
  vertical-align: top;
}

section {
  background-color: #EEE;
  padding-bottom: 20px;
}

.image-container {
  transform: scale;
  transition: .3s transform;
}

.image-container:hover {
  transform: scale(1.25);
}

.trending-container {
  margin-top: 14px;
}

footer {
  background-color: $black;
  width: 100%;
}

.box {
  background-color: #bbb;
  margin: 10px 15px 10px 0px;
  display: inline-block;
}

.box:hover {
  background-color: orange;
}

.footer {
  text-align: center;
  color: #FFF;
  background-color: $black;
  height: 200px;
  padding: 40px;
  font-size: 48px;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

// sourced
.linear-gradient {
  /* Permalink - use to edit and share this gradient: http://colorzilla.com/gradient-editor/#000000+0,000000+100&0+0,0.65+100 */
  background: -moz-linear-gradient(top, rgba(0,0,0,0) 0%, rgba(0,0,0,0.65) 100%); /* FF3.6-15 */
  background: -webkit-linear-gradient(top, rgba(0,0,0,0) 0%,rgba(0,0,0,0.65) 100%); /* Chrome10-25,Safari5.1-6 */
  background: linear-gradient(to bottom, rgba(0,0,0,0) 0%,rgba(0,0,0,0.65) 100%); /* W3C, IE10+, FF16+, Chrome26+, Opera12+, Safari7+ */
  filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#00000000', endColorstr='#a6000000',GradientType=0 ); /* IE6-9 */
}
</style>
