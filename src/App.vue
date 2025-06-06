<template>
  <main class="min-vh-100 position-relative">
    <div class="img-cont w-100 position-absolute overflow-hidden min-vh-100">
      <img class="img-fluid w-100" src="/images/pattern-hills.svg" alt="">
    </div>
    <span class="text-center text-uppercase d-block">We're launching soon</span>
    <div class="clock my-5 d-flex align-items-center">
      <div class="num-card text-center">
        <div class="days position-relative">
          <h1 class="position-relative">
            {{ days < 10 ? `0${days}` : days }} <div class="card-center position-absolute">
              <span class="bullet"></span>
              <span class="bullet"></span>
        </div>
        </h1>
      </div>
      <span class="text d-block mt-3 text-uppercase">Days</span>
    </div>
    <div class="num-card text-center">
      <div class="hours position-relative">
        <h1 class="position-relative">
          {{ hours < 10 ? `0${hours}` : hours }} <div class="card-center position-absolute">
            <span class="bullet"></span>
            <span class="bullet"></span>
      </div>
      </h1>
    </div>
    <span class="text d-block mt-3 text-uppercase">hours</span>
    </div>
    <div class="num-card text-center">
      <div class="minutes position-relative">
        <h1 class="position-relative">
          {{ minutes < 10 ? `0${minutes}` : minutes }} <div class="card-center position-absolute">
            <span class="bullet"></span>
            <span class="bullet"></span>
      </div>
      </h1>
    </div>
    <span class="text d-block mt-3 text-uppercase">minutes</span>
    </div>
    <div class="sec num-card text-center">
      <div class="seconds position-relative">
        <h1 class="position-relative">
          {{ seconds < 10 ? `0${seconds}` : seconds }} <div class="card-center position-absolute">
            <span class="bullet"></span>
            <span class="bullet"></span>
      </div>
      </h1>
    </div>
    <span class="text d-block mt-3 text-uppercase">seconds</span>
    </div>
    </div>
    <div class="social">
      <i class="fa-brands fa-square-facebook"></i>
      <i class="fa-brands fa-pinterest"></i>
      <i class="fa-brands fa-instagram"></i>
    </div>
  </main>
</template>
<script setup>
import { ref } from 'vue';

// Graduation Date :) ♥
const countDown = new Date("May 20, 2026 15:30:00").getTime()

const days = ref(0)
const hours = ref(0)
const minutes = ref(0)
const seconds = ref(0)


let counter = setInterval(() => {
  let dateNow = new Date().getTime()

  let dateDiff = countDown - dateNow

  days.value = Math.trunc((dateDiff / (1000 * 60 * 60 * 24)))
  hours.value = Math.trunc((dateDiff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60))
  minutes.value = Math.trunc((dateDiff % (1000 * 60 * 60)) / (1000 * 60))
  seconds.value = Math.trunc((dateDiff % (1000 * 60)) / 1000)

  if (days.value <= 0 && hours.value <= 0 && minutes.value <= 0 && seconds.value <= 0) {
    clearInterval(counter)
  }
}, 1000)


</script>
<style lang="scss">
* {
  box-sizing: border-box;
}

:root {
  // ### Primary
  --Grayish-blue: hsl(237, 18%, 59%);
  --Soft-red: hsl(345, 95%, 68%);

  // ### Neutral
  --White: hsl(0, 0%, 100%);
  --Dark-desaturated-blue: hsl(236, 21%, 26%);
  --Very-dark-blue: hsl(235, 16%, 14%);
  --Very-dark-mostly-black-blue: hsl(234, 17%, 12%);
}

body {
  font-family: 'Red Hat Text', sans-serif;
  font-size: 14px;
  background-color: #1e1726;
  background-image: url(/images/bg-stars.svg);
  background-repeat: no-repeat;
}

ul {
  list-style: none;
  padding: 0;
  margin: 0;
}


main {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  gap: 50px;

  .img-cont {
    z-index: -1;
  }

  img {
    object-fit: cover;
    position: absolute;
    bottom: 0;
  }

  span {
    color: var(--White);
    letter-spacing: 5px;
    font-size: 20px;
  }

  .clock {
    gap: 100px;

    .num-card {
      .text {
        color: var(--Grayish-blue);
        font-size: 10px;
      }

      .seconds {
        transition: 0.2s;
      }

      .card-center {
        height: 20px;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        width: 150px;
        z-index: 55555555555;
        overflow: hidden;

        &::before {
          content: "";
          position: absolute;
          left: 0;
          top: 50%;
          transform: translateY(-50%);
          background-image: linear-gradient(to bottom, rgb(30, 31, 49), rgb(60, 63, 94));
          width: 100%;
          height: 2px;
        }

        .bullet {
          position: absolute;
          width: 12px;
          height: 12px;
          display: block;
          background-color: var(--Very-dark-mostly-black-blue);
          border-radius: 50%;
          top: 50%;
          transform: translateY(-50%);
          z-index: 555555;

          &:first-of-type {
            left: -7.5px;
          }

          &:last-of-type {
            right: -7.5px;
          }
        }
      }

      h1 {
        color: var(--Soft-red);
        position: relative;
        width: 100px;
        height: 125px;
        display: flex;
        align-items: center;
        justify-content: center;
        z-index: 555;
        font-size: 55px;

        &::before {
          content: "";
          position: absolute;
          width: 150px;
          height: 50%;
          top: 0;
          left: 50%;
          transform: translateX(-50%);
          background-color: rgb(36, 37, 59);
          border-top-right-radius: 5px;
          border-top-left-radius: 5px;
          z-index: -1;
        }

        &::after {
          content: "";
          position: absolute;
          width: 150px;
          height: 50%;
          bottom: 0;
          left: 50%;
          transform: translateX(-50%);
          background-color: var(--Dark-desaturated-blue);
          border-bottom-left-radius: 5px;
          border-bottom-right-radius: 5px;
          z-index: -1;
          box-shadow: 0 8px 0px #14131b;
        }
      }
    }
  }

  .social {
    position: relative;
    z-index: 150000;
    top: 50px;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 25px;

    i {
      color: var(--Grayish-blue);
      font-size: 25px;
      cursor: pointer;
      transition: 0.2s;

      &:hover {
        color: var(--Soft-red);
      }
    }
  }

  @media (max-width: 767px) {
    .img-cont {
      position: relative;
      z-index: -1;

      img {
        max-width: 250% !important;
      }
    }

    .clock {
      gap: 15px;
    }

    .num-card {
      .card-center {
        width: 100% !important;

        .bullet {
          width: 10px !important;
          height: 10px !important;

          &:first-of-type {
            left: -6px !important;
          }

          &:last-of-type {
            right: -6px !important;
          }
        }
      }

      h1 {
        width: 75px !important;
        font-size: 35px !important;
        height: 70px !important;

        &::after,
        &::before {
          width: 100% !important;
        }
      }

      .text {
        font-size: 7px !important;
      }
    }
  }
}
</style>