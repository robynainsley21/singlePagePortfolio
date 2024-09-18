<template>
  <div class="row" id="resume">
    <h4 class="display-2 text-center p-4">Education</h4>

    <div class="row gap-4" v-if="education?.length">
      <div class="edu-box" v-for="edu in education" :key="edu.id">
        <div class="col-item">
          <img :src="edu.img_url" alt="edu-img" loading="lazy" />
        </div>
        <div class="desktop-divider"></div>
        <div class="col-item">
          <p class="card-title">{{ edu.edu_name }}</p>
          <p>{{ edu.date }}</p>
          <p>{{ edu.details[0] }}</p>
          <a href="edu.site"><button>Visit</button></a>
        </div>

        <div class="mobile-divider"></div>
      </div>
    </div>
    <div v-else class="d-flex justify-content-center">
      <div class="spinner-border" role="status"></div>
    </div>
    <h4 class="text-center p-4">Experiences</h4>

    <div class="row gap-3" v-if="experiences?.length">
      <div class="edu-box" v-for="item in experiences" :key="item.id">
        <div class="col-item">
          <img class="col-6 edu-img" :src="item.img_url" :alt="item.company" />
        </div>
        <div class="desktop-divider"></div>
          <div class="col-item">
            <p class="card-title">{{ item.company }}</p>
          <p>{{ item.title }}</p>
          <p>{{ item.duration }}</p>
          <a href="item.site"><button>Visit</button></a>
        </div>
      </div>
      <div class="mobile-divider"></div>
    </div>
    <SpinnerComp v-else />
  </div>
</template>

<script setup>
import SpinnerComp from "@/components/Spinner.vue";
import { computed, onMounted } from "vue";
import { useStore } from "vuex";
const store = useStore();
const education = computed(() => store.state.education);
const experiences = computed(() => store.state.experiences);

onMounted(() => {
  store.dispatch("fetchEducation");
});

onMounted(() => {
  store.dispatch("fetchExperiences");
});
</script>

<style scoped>
#resume {
  background: radial-gradient(ellipse at bottom, #1b2735 0%, #090a0f 100%);
  color: #f5f7f8;
}

:is(img[alt="edu-img"], .edu-img) {
  width: 9rem;
  margin: auto;
  border-radius: 10px;
}

.edu-box {
  display: flex;
  border-radius: 1rem;
  width: 80%;
  margin: 3rem auto;
}

.col-item {
  width: 50%;
}

/**button */
/* From Uiverse.io by adamgiebl */
button {
  --purple: #5a639c;
  padding: 0.6rem 1.5rem;
  letter-spacing: 0.08em;
  position: relative;
  font-family: inherit;
  border-radius: 0.6em;
  overflow: hidden;
  transition: all 0.3s;
  border: 2px solid var(--purple);
  background: linear-gradient(
    to right,
    rgba(155, 126, 218, 0.1) 1%,
    transparent 40%,
    transparent 60%,
    rgba(155, 126, 218, 0.1) 100%
  );
  color: var(--purple);
  box-shadow: inset 0 0 10px rgba(155, 126, 218, 0.4),
    0 0 9px 3px rgba(155, 126, 218, 0.1);
}

button:hover {
  color: #bfa3f3;
  box-shadow: inset 0 0 10px rgba(155, 126, 218, 0.6),
    0 0 9px 3px rgba(155, 126, 218, 0.2);
}

button:before {
  content: "";
  position: absolute;
  left: -4em;
  width: 4em;
  height: 100%;
  top: 0;
  transition: transform 0.4s ease-in-out;
  background: linear-gradient(
    to right,
    transparent 1%,
    rgba(155, 126, 218, 0.1) 40%,
    rgba(155, 126, 218, 0.1) 60%,
    transparent 100%
  );
}

button:hover:before {
  transform: translateX(15em);
}
/**button */

/**mobile */
@media (width < 426px) {
  .edu-box {
    display: flex;
    flex-direction: column;
    justify-content: center;
    text-align: center;
  }

  .mobile-divider {
    width: 50%;
    height: 1px;
    margin: 2rem auto;
    border: 1px solid #f5f7f8;
  }

  .col-item{
    margin: auto;
    width: 100%;
  }
}

/**tablet */
@media (max-width: 769px) and (min-width: 426px) {
  .edu-box {
    display: flex;
    flex-direction: column;
    width: 70%;
    justify-content: center;
    align-items: center;
    margin: auto;
    text-align: center;
  }

  .mobile-divider {
    width: 70%;
    height: 5px;
    margin: 2rem auto;
    /* border: 1px solid #f5f7f8; */
    background: linear-gradient(
      to right,
      transparent 1%,
      rgba(155, 126, 218, 0.1) 40%,
      rgba(155, 126, 218, 0.1) 60%,
      transparent 100%
    );
  }
}

/**desktop */
@media screen and (min-width: 768px) {
    .desktop-divider {
    height: 8rem;
    width: 5px;
    margin: auto 2rem;
    /* border: 1px solid #f5f7f8; */
    background: linear-gradient(
      to right,
      transparent 1%,
      rgba(155, 126, 218, 0.1) 40%,
      rgba(155, 126, 218, 0.1) 60%,
      transparent 100%
    );
  }
}
/**desktop */
</style>
