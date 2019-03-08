<template>

<div>

<carousel v-if="showCarousel"
   :navigationEnabled="true"
   :paginationEnabled="true"
   :perPage="1"
   paginationColor="#D4D3D3"
   >

<slide>
<div id="promo" class="text-vertical-center">
 <ul style="list-style:none">
  <li>You get an experienced IT professional</li>
  <li>You get a proven leader</li>
  <li>You get a knowledgeable consultant</li>
  <li>You get a project manager</li>
  <li>You get a developer near Philly</li>
  <li>You get <span style="text-decoration: underline">two days free</span>, when you add Ken Mills to your project</li>
  </ul>
</div>
</slide>

<slide>
<h4>You get a Laravel developer</h4>
<pre class="laravel-pre"><code class="laravel-code">
class ProjectController extends Controller {
  public function insert(Request $request, Project $project){
    $developer = new User();
    $developer->name = $request->input('name');
    $developer->experience = '10';
    $developer->communication = '10';
    $developer->leadership = '10';
    $developer->save();
    $project->add($developer);
    return response()->json([
      'status' => 'great',
      'getProjectDone' => $developer;
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
        @click = "add( project.id, 'Ken Mills' )"
      &gt;
      &lt;/strong&gt;
    &lt;/li&gt;
  &lt;/ul&gt;
&lt;/div&gt;
</code></pre>
</slide>

<slide>
<h4>You get an experienced Back-Office developer</h4>
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
      showCarousel:true,
    }
  },

}
</script>

<style>

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

</style>
