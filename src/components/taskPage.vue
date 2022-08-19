<template>
  <div class="taskPage">
    <div class="container">
      <div class="row">
        <div class="col">
          <h2 class="tasrPage_h2">
            tasks
          </h2>
        </div>
        <h6 class="taskPage_subtitle"><br>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Quisquam, repellat
          <hr>
        </h6>
      </div>
      <div class="row">
        <div class="col-xl-3 col-lg-6 col-md-6 col-sm-10" v-for="t in task" :key="t.id">
          <div class="taskPage__col">
            <div class="taskPage__centered">
              <h4>{{ t.id }} {{ t.title }}</h4>
              <h6>{{ t.category }}</h6>
              <p>{{ t.dateBegin }} {{ t.dateEnd }}</p>
              <p>{{ t.price }}</p>
              <a class="taskPage__btn" href="#"><span></span><span></span><span></span><span></span> more</a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      task: []
    }
  },
  methods: {
    async getPosts () {
      const offers = await fetch('http://api.staging.umeu.app/test/tasks/search?pagingCount=50&pagingAfter=0')
        .then(response => response.json())
        .then(data => this.task = data.result.offers) // eslint-disable-line
      return (offers)
    }
  },
  mounted () {
    this.getPosts()
  }
}
</script>
