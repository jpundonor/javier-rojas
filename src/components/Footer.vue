<template>
  <footer>
    <div class="footer">
      <div class="footer__container">
        <div class="footer__info">
          <h3 class="footer__title">Javier Rojas</h3>
          <p>{{ $t('footer.description') }}</p>
        </div>
        <div>
          <h3 class="footer__title">Social</h3>
          <ul class="footer__social">
            <li>
              <a
                href="https://www.linkedin.com/in/javier-rojas-43324b143/"
                target="_blank"
                ><i class="fa-brands fa-linkedin"></i
              ></a>
            </li>
            <li>
              <a href="https://github.com/jpundonor" target="_blank"
                ><i class="fa-brands fa-github"></i
              ></a>
            </li>
            <li>
              <a href="https://www.instagram.com/jpundonor/" target="_blank"
                ><i class="fa-brands fa-instagram"></i
              ></a>
            </li>
          </ul>
        </div>
      </div>
      <div class="footer__copy">
        <p>&copy; 2024 Javier Rojas</p>
      </div>
    </div>
  </footer>
</template>

<script></script>

<style scoped>
.footer {
  @apply flex flex-col items-center pt-12 p-4 md:p-8 md:px-14 text-yellow-300 bg-slate-600 bg-opacity-60 backdrop-blur-md;
}
.footer__container {
  @apply flex justify-between w-full border-b-2 pb-6;
}
.footer__info {
  @apply md:w-1/3 w-8/12;
}
.footer__social {
  @apply flex gap-5 text-2xl;
  & li {
    @apply hover:scale-125 transition-transform duration-500;
  }
}
.footer__title {
  @apply text-2xl py-3 font-semibold w-full;
}
.footer__copy {
  @apply py-5 text-sm;
}
</style>
