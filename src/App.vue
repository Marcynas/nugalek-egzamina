<script setup>
import emailjs from "@emailjs/browser";
import { ref } from "vue";
import { Transition } from "vue";

//variables
let formaVardas = ref("");
let formaPavarde = ref("");
let formaZinute = ref("");
//is email sent
let isEmailSent = ref(false);

// scrolled
let scrolled = ref(false);

// detect scroll and change nav button svg
window.addEventListener("scroll", function () {
  if (window.scrollY > 900) {
    scrolled.value = true;
  } else {
    scrolled.value = false;
  }
  console.log(scrolled.value);
});

const sendEmail = (e) => {
  e.preventDefault();
  emailjs
    .send(
      "service_ylyp7l9",
      "template_851n5yn",
      {
        first_name: formaVardas.value,
        last_name: formaPavarde.value,
        message: formaZinute.value,
      },
      "YGc1JE5mTUMz5XjGV"
    )
    .then(
      function (response) {
        console.log("SUCCESS!", response.status, response.text);
        isEmailSent.value = true; // Update the isEmailSent ref value here
      },
      function (error) {
        console.log("FAILED...", error);
      }
    );
};
</script>
<template>
  <body
    class="leading-normal tracking-normal text-white bg-[#a435f0] select-none"
    style="font-family: 'Source Sans Pro', sans-serif"
  >
    <nav id="header" class="fixed w-full z-30 top-0 text-white bg-transparent">
      <div
        class="w-full container mx-auto flex flex-wrap items-center justify-between mt-0 py-2"
      >
        <div class="pl-4 flex items-center">
          <a
            class="toggleColour text-white no-underline hover:no-underline font-bold text-2xl lg:text-4xl"
            href="#"
          >
            Nugalėk Egzaminą
          </a>
        </div>

        <div
          class="w-full flex-grow lg:flex lg:items-center lg:w-auto hidden mt-2 lg:mt-0 bg-white lg:bg-transparent text-black p-4 lg:p-0 z-20"
          id="nav-content"
        >
          <ul
            class="lg:flex justify-end flex-1 items-center text-white text-xl font-bold pt-4 lg:pt-0"
          >
            <button
              onclick="
            //scroll down 1000px
            if (window.scrollY > 900) {
              window.scrollTo({
              top: 0,
              behavior: 'smooth'
            });
            } else {
              window.scrollTo({
              top: 1000,
              behavior: 'smooth'
            });
            }
            "
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke-width="1.5"
                stroke="currentColor"
                class="w-6 h-6"
              >
                <path
                  v-if="scrolled === true"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  d=" M19.5 15.75l-7.5-7.5-7.5 7.5"
                />
                <path
                  v-else
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  d="M19.5 8.25l-7.5 7.5-7.5-7.5"
                />
              </svg>
            </button>
          </ul>
        </div>
      </div>
    </nav>
    <img class="select-none" alt="Welcome" src="./assets/welcome.svg" />
    <br />
    <div class="mt-60 mb-60 w-screen">
      <div class="flex flex-col justify-center items-center h-full w-full">
        <h1 class="text-5xl font-bold">Mokomės kartu</h1>
        <h2 class="text-3xl font-bold">susisiekite</h2>
        <!--Grid with two columns, two people-->
        <div class="sm:grid-cols-3 sm:grid">
          <div
            class="border-2 border-white rounded-lg flex flex-col justify-center items-center m-10 rounded-lg shadow-lg p-8"
          >
            <img
              class="h-32 w-32 rounded-full"
              alt="teacher"
              src="./assets/Mokytojas.jpeg"
            />
            <h3 class="text-2xl font-bold">Domas Kruonis</h3>
            <h4 class="text-xl font-bold">Lietuvių kalba</h4>
            <p class="text-lg">+37062569014</p>
            <p class="text-lg">
              <a href="mailto:Domas.Kruonis@NugalekEgzamina.com">
                Domas.Kruonis@NugalekEgzamina.com
              </a>
            </p>
          </div>
          <div
            class="border-2 border-white rounded-lg flex flex-col justify-center items-center m-10 rounded-lg shadow-lg p-8"
          >
            <img
              class="h-32 w-32 rounded-full"
              alt="teacher"
              src="./assets/Mokytojas2.jpeg"
            />
            <h3 class="text-2xl font-bold">Kipras Batis</h3>
            <h4 class="text-xl font-bold">Istorija</h4>
            <p class="text-lg">+37062569013</p>
            <p class="text-lg">
              <a href="mailto:Kipras.Batis@NugalekEgzamina.com">
                Kipras.Batis@NugalekEgzamina.com
              </a>
            </p>
          </div>
          <div
            class="border-2 border-white rounded-lg flex flex-col justify-center items-center m-10 rounded-lg shadow-lg p-8"
          >
            <img
              class="h-32 w-32 rounded-full"
              alt="teacher"
              src="./assets/Mokytojas3.jpeg"
            />
            <h3 class="text-2xl font-bold">Ana Jurgelaite</h3>
            <h4 class="text-xl font-bold">Chemija</h4>
            <p class="text-lg">+37062569012</p>
            <p class="text-lg">
              <a href="mailto:Ana.Jurgelaite@NugalekEgzamina.com">
                Ana.Jurgelaite@NugalekEgzamina.com
              </a>
            </p>
          </div>
        </div>
        <button
          class="animate-bounce mt-20"
          onclick="
            window.scrollTo({
              top: 2000,
              behavior: 'smooth'});
            "
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            stroke-width="1.5"
            stroke="currentColor"
            class="w-6 h-6"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M19.5 13.5L12 21m0 0l-7.5-7.5M12 21V3"
            />
          </svg>
        </button>
      </div>
    </div>

    <div class="mt-20 w-screen">
      <div class="flex flex-col justify-center items-center h-full w-full">
        <h1 class="text-5xl font-bold">Atsiliepimai</h1>
        <h2 class="text-3xl font-bold">iš mūsų mokinių</h2>

        <!--grid 2 cols. form to leave / place to read -->
        <div class="sm:grid-cols-2 sm:grid">
          <!--form to write atsiliepimas-->
          <div class="flex flex-col justify-center items-center m-10">
            <h3 class="text-2xl font-bold mb-5">Palik atsiliepimą ir tu 😉</h3>
            <!--view if email is sent-->
            <Transition name="fade" mode="out-in" appear>
              <div v-if="isEmailSent">
                <h3 class="text-2xl font-bold mb-5">Ačiū už atsiliepimą!</h3>
              </div>
              <div v-else>
                <form
                  class="text-white flex flex-col justify-center items-center"
                  @submit="sendEmail"
                >
                  <!--row for vardas and pavarde-->
                  <div class="flex flex-row justify-center items-center">
                    <div class="flex flex-col justify-center items-center m-2">
                      <label class="text-xl font-bold" for="vardas"
                        >Vardas</label
                      >
                      <input
                        class="border-2 border-white rounded-lg p-2 m-2 text-black"
                        type="text"
                        id="vardas"
                        v-model="formaVardas"
                        required
                      />
                    </div>
                    <div class="flex flex-col justify-center items-center m-2">
                      <label class="text-xl font-bold" for="pavarde"
                        >Pavardė</label
                      >
                      <input
                        class="border-2 border-white rounded-lg p-2 m-2 text-black"
                        type="text"
                        id="pavarde"
                        v-model="formaPavarde"
                        required
                      />
                    </div>
                  </div>
                  <!--row for zinute-->
                  <div class="flex flex-col justify-center items-center m-2">
                    <label class="text-xl font-bold" for="zinute">Žinutė</label>
                    <textarea
                      class="border-2 border-white rounded-lg p-2 m-2 text-black"
                      id="zinute"
                      cols="60"
                      rows="10"
                      v-model="formaZinute"
                      required
                    ></textarea>
                  </div>
                  <button
                    class="border-2 border-white rounded-lg p-2 m-2"
                    type="submit"
                  >
                    Siųsti
                  </button>
                </form>
              </div>
            </Transition>
          </div>
          <!--place to read atsiliepimas-->
          <div class="grid grid-cols-2 justify-center items-center m-10">
            <div class="p-8 m-5 border-2 border-white rounded-lg shadow-lg">
              <h4 class="text-xl font-bold">Domas Kisielius</h4>
              <p class="text-lg">
                Mano patirtis su korepetitoriumi buvo labai teigiama. Ji buvo
                labai kantri ir supratinga, padėjo man suprasti sudėtingus
                dalykus ir užtikrino, kad aš gerai pasirengčiau egzaminams. Ačiū
                jai, pasiekiau gerų rezultatų ir labai rekomenduočiau šį
                korepetitorį kitiems studentams.
              </p>
            </div>
            <div class="p-8 m-5 border-2 border-white rounded-lg shadow-lg">
              <h4 class="text-xl font-bold">Kipras Danelovič</h4>
              <p class="text-lg">
                Mano korepetitorius buvo tikras radojimas. Jis buvo pasirengęs
                skirti papildomą laiką, kad paaiškintų sunkumus, kuriuos aš
                patyriau, ir visada buvo pasirengęs atsakyti į mano klausimus.
                Mano pažymiai pagerėjo nuo to laiko, kai pradėjau su juo dirbti,
                ir aš neabejotinai rekomenduočiau jį visiems, ieškantiems
                efektyvaus ir motyvuojančio korepetitoriaus.
              </p>
            </div>
            <div class="p-8 m-5 border-2 border-white rounded-lg shadow-lg">
              <h4 class="text-xl font-bold">Antanas Gairys</h4>
              <p class="text-lg">
                Turėjau tik teigiamų įspūdžių apie korepetitoriaus paslaugas. Ji
                buvo labai organizuota, struktūruota ir pasiruošusi kiekvienam
                mūsų užsiėmimui. Ji sukūrė individualizuotą mokymo planą,
                atsižvelgdama į mano stipriąsias ir silpnąsias sritis, ir
                stengėsi sukurti palankią ir produktyvią mokymo aplinką. Dėl jos
                pagalbos aš jaučiausi pasitikintis ir pasiekiau gerų rezultatų.
                Aš nuoširdžiai rekomenduočiau šią korepetitorę visiems,
                ieškantiems padėties mokantis.
              </p>
            </div>
            <div class="p-8 m-5 border-2 border-white rounded-lg shadow-lg">
              <h4 class="text-xl font-bold">Justė Gačnaitė</h4>
              <p class="text-lg">
                Mano patirtis su korepetitoriumi buvo labai teigiama. Ji buvo
                labai kantri ir supratinga, padėjo man suprasti sudėtingus
                dalykus ir užtikrino, kad aš gerai pasirengčiau egzaminams. Ačiū
                jai, pasiekiau gerų rezultatų ir labai rekomenduočiau šį
                korepetitorį kitiems studentams.
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </body>
</template>

<!-- animate transition -->
<style>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
