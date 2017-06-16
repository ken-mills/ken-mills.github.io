<template>

<div>

<div id="projects" v-if="showForm">

      <table>
      <tr v-for="project in projects">
          <td>
              <div class="truncate">
                <span>Add a Ken Mills to your </span>
                <span :class="{'laravel-code': project.isLaravel, 'vue-code': !project.isLaravel}">
                  {{project.name}}
                </span>
                <span class="truncated"> project </span>
              </div>
          </td>
          <td>
            <a>
               <i class="fa fa-plus fa-lg" aria-hidden="true" v-on:click="addTeamMember(project.id)"
                   rel="tooltip" title="Add Ken MIlls"></i>
            </a>
          </td>

      </tr>
      </table>
</div>

  <carousel v-if="showCarousel" :navigationEnabled="false" pagination="true" perPage="1" paginationColor="#D4D3D3" >


  <slide>
  <pre class="vue-pre"><code class="vue-code">
  &lt;div v-if="showProjects"&gt;
    &lt;ul&gt;
      &lt;li v-for = "project in projects"&gt;
        &lt;strong
          class="fa fa-plus" aria-hidden="true"
          @click = "addTeamMember( project.id, 'Ken Mills' )"
        &gt;
        &lt;/strong&gt;
      &lt;/li&gt;
    &lt;/ul&gt;
  &lt;/div&gt;
  </code></pre>
  </slide>

  <slide>
  <pre class="laravel-pre"><code class="laravel-code">
  class ProjectController extends Controller {
    public function AddTeamMember(Request $request, Project $project){
      $new_team_member = new User();
      $new_team_member->name = $request->input('name');
      $new_team_member->save();
      $project->add_member($new_team_member);
      return response()->json([
        'status' => 'ok',
        'newTeamMember' => $new_team_member;
      ]);
    }
  }
  </code></pre>
  </slide>

  <slide>
  <div id="promo">
    <h4><span style="text-decoration: underline">One week free</span>, when you add Ken Mills to your team</h4>
    <h4>Available for remote projects or onsite projects near Philly</h4>
  </div>
  </slide>

  </carousel>

</div>
</template>

<script>
import { Carousel, Slide } from 'vue-carousel';

export default {
  name: 'app',
  components: {
    Carousel,
    Slide
  },
  data: function () {
    return {
      showForm: true,
      showCarousel:false,
      projects: [

        {"id":0, "name" : "Laravel" , "isLaravel" : true },
        {"id":1, "name" : "Vue.js", "isLaravel" : false },

      ]
    }
  },

  mounted: function () {
    this.showForm = true;
  },

  methods: {

    addTeamMember: function(id){

      console.log('Button clicked = ' + id);
      this.showForm = false;
      this.showCarousel = true;
    }

  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
  text-align: left;
}

.truncate {
    display: table;
    table-layout: fixed;
    width: 100%;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    font-weight: bold;
    margin-top: 15px;

}

.truncated:after {
    content:'................................................................................................................................';
}

.vue-pre{
  background-color: white;
  min-height: 275px;
  border:0;
}

.vue-code {
  color: #41b883;
  font-size: 110%;
  font-weight: 600;
}

.laravel-pre{
  background-color: white;
  min-height: 275px;
  border:0;
}

.laravel-code {
  color: #f35045;
  font-size: 110%;
  font-weight: 600;
}

#promo h4{
  padding-top: 3px;
  color:#2c3e50;
  text-align: left;
}

#projects table {
  font-size: 120%;
}

a:hover {
 cursor:pointer;
}
</style>
