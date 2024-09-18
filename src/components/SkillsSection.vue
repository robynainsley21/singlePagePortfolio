<template>
  <div v-if="skills?.length" class="row gap-3">
    <div class="card col-md-4" v-for="skill in skills" :key="skill.id">
      <div class="content">
        <div class="back">
          <div class="back-content">
            <div class="icon mt-4">
              <img class="m-auto" :src="skill.img_url" alt="skill-img" />
            </div>
            <strong>{{ skill.skill }}</strong>
          </div>
        </div>
        <div class="front">
          <div class="img">
            <div class="circle"></div>
            <div class="circle" id="right"></div>
            <div class="circle" id="bottom"></div>
          </div>

          <div class="front-content">
            <div class="description">
                {{ skill.description }}
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  <SpinnerComp v-else />
</template>

<script setup>
import SpinnerComp from "@/components/Spinner.vue";
import { computed, onMounted } from "vue";
import { useStore } from "vuex";
const store = useStore();
const skills = computed(() => store.state.skills);

onMounted(() => {
  store.dispatch("fetchSkills");
});
</script>

<style scoped>
img[alt="skill-img"] {
  width: 5rem;
}

/**card */
strong{
    top: 0;
}
/* From Uiverse.io by ElSombrero2 */
.card {
  overflow: visible;
  width: 18rem;
  height: 300px;
  margin: auto;
  border: none;
}

.content {
  width: 100%;
  height: 100%;
  transform-style: preserve-3d;
  transition: transform 300ms;
  box-shadow: 0px 0px 10px 1px #000000ee;
  border-radius: 5px;
}

.front,
.back {
  background-color: #151515;
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
  -webkit-backface-visibility: hidden;
  border-radius: 5px;
  overflow: hidden;
}

.back {
  width: 100%;
  height: 100%;
  justify-content: center;
  display: flex;
  align-items: center;
  overflow: hidden;
}

.back::before {
  position: absolute;
  content: " ";
  display: block;
  width: 160px;
  height: 160%;
  background: linear-gradient(
    90deg,
    transparent,
    #5a639c,
    #5a639c,
    #5a639c,
    #5a639c,
    transparent
  );
  animation: rotation_481 5000ms infinite linear;
}

.back-content {
  position: absolute;
  padding: 2rem;
  width: 97.5%;
  height: 97.5%;
  background-color: #151823;
  border-radius: 5px;
  color: white;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;
  gap: 30px;
}

.card:hover .content {
  transform: rotateY(180deg);
}

@keyframes rotation_481 {
  0% {
    transform: rotateZ(0deg);
  }

  0% {
    transform: rotateZ(360deg);
  }
}

.front {
  transform: rotateY(180deg);
  color: white;
}

.front .front-content {
  position: absolute;
  width: 100%;
  height: 100%;
  padding: 10px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.front-content .badge {
  background-color: #00000055;
  padding: 2px 10px;
  border-radius: 10px;
  backdrop-filter: blur(2px);
  width: fit-content;
}

.description {
    height: 99%;
  box-shadow: 0px 0px 10px 5px #00000088;
  width: 100%;
  padding: 10px;
  background-color: #00000099;
  backdrop-filter: blur(5px);
  border-radius: 5px;
}

.front .img {
  position: absolute;
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
}

.circle {
  width: 90px;
  height: 90px;
  border-radius: 50%;
  background-color: #5a639c;
  position: relative;
  filter: blur(15px);
  animation: floating 2600ms infinite linear;
}

#bottom {
  background-color: #5a639c;
  left: 50px;
  top: 0px;
  width: 150px;
  height: 150px;
  animation-delay: -800ms;
}

#right {
  background-color: #5a639c;
  left: 160px;
  top: -80px;
  width: 30px;
  height: 30px;
  animation-delay: -1800ms;
}

@keyframes floating {
  0% {
    transform: translateY(0px);
  }

  50% {
    transform: translateY(10px);
  }

  100% {
    transform: translateY(0px);
  }
}
/**card */

/**mobile */
@media screen and (max-width: 426px) {
    .card{
        width: 16rem;
    }


}
/**mobile */
</style>
