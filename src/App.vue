<template>
<carousel :navigationEnabled="false" :pagination="true" :perPage="1" >

<slide>
<div id="projects">
<ul>
  <li>
    Your Laravel Project
  </li>
  <li>Your Vue.js Project</li>
</ul>
</div>
</slide>


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
  <h4>One week free, when you add Ken Mills to your team</h4>
  <h4>Available for remote projects or local projects near Philly</h4>
</div>
</slide>

</carousel>
</template>

<script>
import { Carousel, Slide } from 'vue-carousel';

export default {
  name: 'app',
  components: {
    Carousel,
    Slide
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  text-align: left;
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

#projects ul {
  list-style:none;
  font-size: 120%;
}
#projects li {
  padding-top:10px;
  font-weight: 600;
}

</style>
