<template>
  <div class="RecentProjects container" id="projects">
    <h2 class="text-center display-4">Recent Projects</h2>

    <div class="row">
      <div class="project col-sm-12 col-md-6">
        <a href="#" target="_blank">
          <div class="card">
            <h3 class="project-title">Title</h3>
            <button class="btn btn-outline-primary" id="#link">View Project</button>
          </div>
        </a>
      </div>
      <div class="project col-sm-12 col-md-6">
        <a href="#" target="_blank">
          <div class="card">
            <h3 class="project-title">Title</h3>
            <button class="btn btn-outline-primary" id="#link">View Project</button>
          </div>
        </a>
      </div>
      <div class="project col-sm-12 col-md-6">
        <a href="#" target="_blank">
          <div class="card">
            <h3 class="project-title">Title</h3>
            <button class="btn btn-outline-primary" id="#link">View Project</button>
          </div>
        </a>
      </div>
      <div class="project col-sm-12 col-md-6">
        <a href="#" target="_blank">
          <div class="card">
            <h3 class="project-title">Title</h3>
            <button class="btn btn-outline-primary" id="#link">View Project</button>
          </div>
        </a>
      </div>
    </div>

        <!-- <div v-for="post in $static.posts.nodes" :key="post.id" class="project col-sm-12 col-md-6">
          <a :href="post.acfpost.link" target="_blank">
            <div class="card">
              <h3 class="project-title">{{ post.title }}</h3>
              <img
                v-if="post.acfpost"
                :alt="post.title"
                :src="post.acfpost.screenshot.mediaItemUrl"/>
              <button class="btn btn-outline-primary" id="#link">View Project</button>
              <p v-html="post.node.content"></p>
            </div>
          </a>
        </div> -->

  </div>
</template>

<script>
  export default {
    name: 'RecentProjects'
  }
</script>

<style scoped>
  h3 {
    margin: 40px 0 0;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    display: inline-block;
    margin: 0 10px;
  }
  a {
    color: #42b983;
  }
</style>
