<template>
  <carousel :navigationEnabled="false" :pagination="true" :perPage="1" >
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
}

.vue-pre{
  background-color: #35495e;
  min-height: 275px;
}

.vue-code {
  color: #41b883;
  font-size: 110%;
  font-weight: 600;
}

.laravel-pre{
  background-color: white;
  min-height: 275px;
}

.laravel-code {
  color: #f35045;
  font-size: 110%;
  font-weight: 600;
}

</style>
