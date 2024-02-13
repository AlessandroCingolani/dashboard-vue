<script>
export default {
  name:'HeaderComponent',
}
</script>


<template>
  <header>
    <div class="container-fluid h-100 d-flex justify-content-between align-items-center">
      <i class="fa-solid fa-bars"></i>
      <div class="logged-profile d-flex align-items-center ">
        <i class="fa-regular fa-envelope"></i>
        <img src="https://cdn.iconscout.com/icon/free/png-256/free-avatar-370-456322.png?f=webp" alt="profile-img">
        
        <!-- dropdown -->
        <span class="dropdown me-2">
          <a class="text-decoration-none" href="#" role="button" data-bs-toggle="dropdown" aria-expanded="false">
            <span>Mario Rossi</span>
            <i class="fa-solid fa-chevron-down"></i>
          </a>
          <ul class="dropdown-menu mt-3">
            <li><a class="dropdown-item" href="#">Profile</a></li>
            <li><a class="dropdown-item" href="#">Logout</a></li>
          </ul>
        </span>
      </div>
    </div>
  </header>
</template>


<style lang="scss" scoped>
  .fa-bars {
    color: rgb(103, 116, 130);
    font-size: 1.4rem;
  }
  .logged-profile {
    img {
      width: 30px;
      height: 30px;
      margin: 0 10px;
    }
    span,i {
      color: rgb(156, 164, 174);
    }
  }
</style>