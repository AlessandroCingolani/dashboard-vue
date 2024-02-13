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
        <span class="fs-5">Welcome</span>
        <h5 class="fw-medium">Mario Rossi</h5>
      </div>
    </div>
    <!-- general -->
    <nav>
      <div class="general">
        <h5 class="text-uppercase pb-1">general</h5>
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
              <i class="fa-solid fa-map-location-dot"></i> Maps
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
              <i class="fa-solid fa-gear"></i> Config
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
              <i class="fa-solid fa-envelope"></i> Contacts
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
    font-size: 1.3rem;
    &::before {
      content: " - ";
    }
    &::after{
      content: " - ";
    }
  }

  .welcome {
    span {
      opacity: 0.7;
      font-size: 1.2rem;
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
      border-bottom: 3px solid white;
    }
    .accordion{
      margin-top: 20px;
      --bs-accordion-btn-bg: rgb(42, 64, 84);
      --bs-accordion-btn-color: white;
      --bs-accordion-btn-focus-box-shadow: none;
      --bs-accordion-border-color: none;
      --bs-accordion-active-color: rgb(42, 64, 84);
      --bs-accordion-bg:  rgb(42, 64, 84);
      --bs-accordion-active-color: white;
      --bs-accordion-active-bg:  rgb(42, 64, 84);
      --bs-accordion-body-padding-x: 0;
      --bs-accordion-btn-padding-x: 0;
      --bs-accordion-btn-padding-y: 10px;
      
      .accordion-button.collapsed::after{
        filter: brightness(0) invert(1) !important;
        
      }
      .accordion-button:not(.collapsed)::after{
        filter: brightness(0) invert(1) !important;

      }
      i {
        padding-right: 20px;
      }
      a {
        text-decoration: none;
        color: white;
        display: inline-block;
        width: 100%;
        padding: 4px 0 4px 40px;
        &:hover{
          background: lighten( rgb(42, 64, 84), $amount: 6);
        }
      }
    }
  }
</style>