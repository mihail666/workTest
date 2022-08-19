<template>
  <div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
    <div class="modal-dialog modal-lg modal-dialog-centered">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="exampleModalLabel">CreatePost</h5>
        </div>
        <div class="modal-body">
          <form @submit.prevent="setPost">
            <div class="mb-3">
                <label for="categoryId">categories:</label>
                <select v-model="postData.categoryId" id="categoryId" class="form-control">
                  <option v-for=" c in categor" :key="c.id">
                    {{ c.title }}
                  </option>
                </select>
            </div>
            <div class="mb-3">
              <label for="title">nameTask:</label>
              <input type="text" id="title" class="form-control" v-model="postData.title">
            </div>
            <div class="mb-3">
              <label for="dateBegin">dateBegin:</label>
              <input type="datetime-local" name="date" id="dateBegin" class="form-control" v-model="postData.dateBegin">
            </div>
            <div class="mb-3">
              <label for="dateEnd">dateEnd:</label>
              <input type="datetime-local" name="date" id="dateEnd" class="form-control" v-model="postData.dateEnd">
            </div>
            <div class="mb-3">
              <label for="price">Price:</label>
              <input id="price" type="text" class="form-control" v-model="postData.price"
                onkeypress="return (event.charCode >= 48 && event.charCode <= 57 && /^\d{0,10}$/.test(this.value));"
                placeholder="0,00$" />
            </div>
            <button type="submit" class="castBtn"><span></span><span></span><span></span><span></span> post
              task</button>
          </form>
        </div>
        <div class="modal-footer">
          <button type="button" class="castBtn"
            data-bs-dismiss="modal"><span></span><span></span><span></span><span></span>Close</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      categor: [],
      postData: {
        dateBegin: '',
        dateEnd: '',
        price: '',
        title: ''
      }
    }
  },
  methods: {
    async getPosts () {
      const categories = await fetch('http://api.staging.umeu.app/test/categories')
        .then(response => response.json())// eslint-disable-next-line
        .then(data => this.categor = data.result.categories)
      // console.log(categories)
    },
    setPost () {
      fetch('http://api.staging.umeu.app/test/task/create/', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify({
          dateBegin: this.dateBegin,
          dateEnd: this.dateEnd,
          price: this.price,
          title: this.title
        })
      })
        .then(response => console.log(response.json()))
        .then(data => console.log(data))
    }
  },
  mounted () {
    this.getPosts()
  }
}
</script>
