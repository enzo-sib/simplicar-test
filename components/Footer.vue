<template>
  <footer class="footer-page">
    <div class="container mx-auto pt-5">
      <div class="row">
        <div
          class="
            col-12
            flex
            flex-col
            sm:flex-row
            items-center
            nissan-logo
            pt-4
            pb-2
          "
        >
          <span class="SFDisplay-heavy pr-3">Nissan. </span>
          Innovation that excites
        </div>
      </div>
      <div class="grid grid-cols-1 md:grid-cols-4 my-3">
        <div class="col-md-3">
          <ul class="list">
            <li class="list-item">
              <p class="list-item-title SFDisplay-bold uppercase">cotización de vehículos</p>
            </li>
            <li class="list-item">
              <div class="flex flex-row items-center gap-1">
                <i class="ri-information-line"></i> 
                <NuxtLink class="list-item-link" to="/informacion-legal">Información Legal</NuxtLink>
              </div>
            </li>
          </ul>
        </div>
        <div class="col-md-3">
          <ul class="list">
            <li class="list-item">
              <p class="list-item-title SFDisplay-bold uppercase">Ralitor S.A.</p>
            </li>
            <li class="list-item">
              <a class="list-item-link" href="https://www.nissan.com.uy">nissan.com.uy</a>
            </li>
            <li class="list-item">
              <NuxtLink class="list-item-link" to="/politicas-cookies">Políticas de Cookies</NuxtLink>
            </li>
          </ul>
        </div>
        <div class="col-md-3">
          <ul class="list">
            <li class="list-item">
              <p class="list-item-title SFDisplay-bold uppercase">Ayuda al Cliente</p>
            </li>
            <li>
              <NuxtLink class="list-item-link" to="/politicas-de-privacidad">Políticas de Privacidad</NuxtLink>
            </li>
          </ul>
        </div>
        <div class="col-md-3">
          <ul class="list">
            <li>
              <p class="list-item-title SFDisplay-bold uppercase">Nissan Social</p>
            </li>
            <li class="flex flex-row items-center">
              <a href="https://www.facebook.com/nissanuruguay" class="list-item-link"> <i class="list-item-icon ri-facebook-fill"></i> </a>
              <a href="https://www.instagram.com/nissanuruguay" class="list-item-link"> <i class="list-item-icon ri-instagram-line"></i> </a>
              <a href="https://www.twitter.com/uruguaynissan" class="list-item-link"> <i class="list-item-icon ri-twitter-fill"></i> </a>
              <a href="https://www.youtube.com/channel/UCvQjL7hfaO3ICXjlgSm3alg" class="list-item-link"> <i class="list-item-icon ri-youtube-fill"></i></a>
            </li>
          </ul>
        </div>
      </div>
    </div>
    <div class="right-divider"></div>
    <div class="container mx-auto pt-4 pb-10">
      <p class="copyright">© 2020 SIMPLICAR. Todos los derechos reservados.</p>
    </div>
  </footer>
</template>

<script>
export default {};
</script>

<style scoped>
.list {
  list-style-type: none;
  margin-left: 0;
  padding: 0;
}
.list-item{
  margin-bottom: 15px;
}
.list-item-icon {
  font-size: 18px;
  margin-right: 10px;
}
.list-item-title {
  font-size: 14px;
  color: #b5b5b5;
}
.list-item-link {
  color: white;
  font-size: 13px;
  font-weight: 400;
  text-decoration: none;
}
.list-item-link:hover{
  color: #fff;
  text-decoration: underline;
}
.right-divider{
  border-top: 1px solid #272727;
}
.footer-page {
  background-color: black;
  color: white;
}
.nissan-logo {
  color: #fff;
  font-size: 25px;
}
.copyright {
  font-size: 13px;
  color: #b5b5b5;
  font-weight: 400;
}
</style>