<template>

<div>

<div id="projects" v-if="showForm1">

      <table>
      <tr v-for="project in sortedProjects">
          <td>
              <div class="truncate">
                Add Ken to your
                <span :class="project.class">
                  {{project.name}}
                </span>
                <span class="truncated"> project </span>
              </div>
          </td>
          <td>
            <a class="btn btn-primary btn-colors" style="margin-left:2px" href="#" v-on:click="addTeamMember(project.id)">
                <i class="fa fa-plus icon-color"
                   rel="tooltip" title="Add Ken Mills"></i>Ken Mills</a>
          </td>

      </tr>
      </table>
</div>

<div id="ken-mills" v-if="showForm2">

  <form method="POST" v-on:submit.prevent="saveTeamMember" class="form-inline" >

  <div class="form-group form-spacing">
    <label for="member">Team Member</label>
    <input type="text" class="form-control" value="Ken Mills" id="member" disabled>
  </div>

  <div class="form-group">
    <input type="submit" value="Add" class="btn btn-primary" />
  </div>

  </form>

</div>

<carousel v-if="showCarousel" :navigationEnabled="true" :paginationEnabled="true" :perPage="1" paginationColor="#D4D3D3" >

<slide>
<div id="promo">
 <ul style="list-style:none">
  <li>You get a team player</li>
  <li>You get an experienced professional</li>
  <li>You get a remote developer or</li>
  <li>You get an onsite developer near Philly</li>
  <li>You get <span style="text-decoration: underline">two days free</span>, when you add Ken Mills to your team</li>

  </ul>
</div>
</slide>

<slide>
<h4>You get a Laravel developer</h4>
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
<h4>You get a Vue.js developer</h4>
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
<h4>You get an experienced database developer</h4>
<pre class="laravel-pre"><code class="laravel-code">
$category_average = Score::where([
    ['scores.survey_id','=', $row->survey_id],
    ['score_items.category_id', '=', $row->id] //category_id ])
  ->leftJoin('score_items', 'score_items.score_id', 'scores.id')
  ->groupBy('scores.survey_id','score_items.category_id')
  ->select(DB::raw('round(avg(score_items.score),0) as avg_score'))
  ->first()->avg_score;</code></pre>
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
      showForm1: true,
      showForm2: false,
      showCarousel:false,
      projects: [

        {"id":0, "name" : "Laravel" , "class" : "laravel-code" },
        {"id":1, "name" : "Vue.js", "class" : "vue-code" },
        {"id":2, "name" : "backoffice", "class": "" },

      ]
    }
  },

  mounted: function () {
    this.showForm1 = true;
  },

  computed: {

    sortedProjects: function(){

        return this.projects.sort(function(a, b){
           return a.id - b.id;
        });

    }

  },

  methods: {

    addTeamMember: function(id){

      console.log('Button clicked = ' + id);
      this.showForm1 = false;
      this.showCarousel = true;
    },

    saveTeamMember: function(id){

      console.log('Button clicked = ' + id);
      this.showForm2 = false;
      this.showCarousel = false;
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
  margin-top: 30px;
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

#promo {
    padding-top: 60px
}

#promo li{
  padding-top: 3px;
  color:#2c3e50;
  font-size: 150%;
  text-align: left;
}

#projects table {
  font-size: 120%;
}

a:hover {
 cursor:pointer;
}

.form-spacing{
  padding-left: 15px;
}

.btn-colors {
  color:white;
  background-color:#2c3e50;
}

.icon-color {
    color: white;
}

</style>
