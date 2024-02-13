  <script>
  export default {
    name:'AsideComponent',
  }
  </script>


<template>
  <aside class="d-flex flex-column ">
    <!-- title -->
    <div class="title">
      <span>Dashboard</span>
    </div>
    <!-- user -->
    <div class="profile my-3 d-flex  align-items-center">
      <img src="https://cdn.iconscout.com/icon/free/png-256/free-avatar-370-456322.png?f=webp" alt="profile-img">
      <div class="welcome">
        <h4>Welcome</h4>
        <h5>Mario Rossi</h5>
      </div>
    </div>
    <!-- general -->
    <nav>
      <div class="general">
        <h5 class="text-uppercase">general</h5>
      </div>
      
      <!-- accordion -->
      <div class="accordion accordion-flush" id="accordion-nav">
        <div class="accordion-item">
          <h2 class="accordion-header">
            <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#flush-collapseOne" aria-expanded="false" aria-controls="flush-collapseOne">
              <i class="fa-solid fa-house-chimney"></i> Home
            </button>
          </h2>
          <div id="flush-collapseOne" class="accordion-collapse collapse" data-bs-parent="#accordionFlushExample">
            <div class="accordion-body">
              <ul class="list-unstyled">
                <li><a href="#">Dashboard</a></li>
                <li><a href="#">Dashboard 1</a></li>
                <li><a href="#">Dashboard 2</a></li>
              </ul>
            </div>
          </div>
        </div>
        <div class="accordion-item">
          <h2 class="accordion-header">
            <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#flush-collapseTwo" aria-expanded="false" aria-controls="flush-collapseTwo">
              <i class="fa-solid fa-house-chimney"></i> Home
            </button>
          </h2>
          <div id="flush-collapseTwo" class="accordion-collapse collapse" data-bs-parent="#accordionFlushExample">
            <div class="accordion-body">
              <ul class="list-unstyled">
                <li><a href="#">Dashboard</a></li>
                <li><a href="#">Dashboard 1</a></li>
                <li><a href="#">Dashboard 2</a></li>
              </ul>
            </div>
          </div>
        </div>
        <div class="accordion-item">
          <h2 class="accordion-header">
            <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#flush-collapseThree" aria-expanded="false" aria-controls="flush-collapseThree">
              <i class="fa-solid fa-house-chimney"></i> Home
            </button>
          </h2>
          <div id="flush-collapseThree" class="accordion-collapse collapse" data-bs-parent="#accordionFlushExample">
            <div class="accordion-body">
              <ul class="list-unstyled">
                <li><a href="#">Dashboard</a></li>
                <li><a href="#">Dashboard 1</a></li>
                <li><a href="#">Dashboard 2</a></li>
              </ul>
            </div>
          </div>
        </div>
        <div class="accordion-item">
          <h2 class="accordion-header">
            <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#flush-collapseFour" aria-expanded="false" aria-controls="flush-collapseFour">
              <i class="fa-solid fa-house-chimney"></i> Home
            </button>
          </h2>
          <div id="flush-collapseFour" class="accordion-collapse collapse" data-bs-parent="#accordionFlushExample">
            <div class="accordion-body">
              <ul class="list-unstyled">
                <li><a href="#">Dashboard</a></li>
                <li><a href="#">Dashboard 1</a></li>
                <li><a href="#">Dashboard 2</a></li>
              </ul>
            </div>
          </div>
        </div>
      </div>
      <!-- / accordion -->
    </nav>
  </aside>
</template>


<style lang="scss" scoped>
  .title{
    &::before {
      content: "-";
    }
    &::after{
      content: "-";
    }
  }

  .profile {

    img{
      width: 60px;
      height: 60px;
      border-radius: 50%;
      overflow: hidden;
      border: 5px solid white;
      margin-right: 20px;
    }
  }

  nav{
    .general {
      border-bottom: 2px solid white;
    }
    .accordion{
      --bs-accordion-btn-bg: rgb(42, 64, 84);
      --bs-accordion-btn-color: white;
      --bs-accordion-btn-focus-box-shadow: none;
      --bs-accordion-border-color: none;
      --bs-accordion-active-color: rgb(42, 64, 84);
      --bs-accordion-bg:  rgb(42, 64, 84);
      --bs-accordion-active-color: white;
      --bs-accordion-active-bg:  rgb(42, 64, 84);
      
      a {
        text-decoration: none;
        color: white;
        display: inline-block;
        width: 100%;
        &:hover{
          background: lighten( rgb(42, 64, 84), $amount: 6);
        }
      }
    }
  }
</style>