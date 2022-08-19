<template>
  <nav class="navbar navbar-expand-lg sticky-top" style="background-color: #1b1b1b;">
    <div class="container">
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav me-auto mb-1 mb-lg-0">
          <li class="nav-item logo">
            <h3>TestWork</h3>
          </li>
          <li>
            <button type="button" class="btn castBtn " data-bs-toggle="modal" data-bs-target="#exampleModal">
            <span></span><span></span><span></span><span></span> Create Task</button>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
</script>

<style lang="scss">
.navbar {
  height: 60px;
  padding: 10px;
}

.logo {
  font-size: 30px;
  padding: 15px;
  transition: .4s;
  font-weight: 500;
  color: #ffffff;
}
</style>
