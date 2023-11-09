<script setup>
import { ref } from "vue";

function triggerMenu() {
  const header = document.querySelector(`.header`);
  header.classList.toggle(`menu-opened`);
}

const headerOptions = ref([
  {
    name: "Features",
    subOptions: [
      {
        name: "Todo List",
        icon: "/assets/icon-todo.svg",
      },
      {
        name: "Calendar",
        icon: "/assets/icon-calendar.svg",
      },
      {
        name: "Reminders",
        icon: "/assets/icon-reminders.svg",
      },
      {
        name: "Planning",
        icon: "/assets/icon-planning.svg",
      },
    ],
  },
  {
    name: "Company",
    subOptions: [
      {
        name: "History",
      },
      {
        name: "Our Team",
      },
      {
        name: "Blog",
      },
    ],
  },
  {
    name: "Careers",
  },
  {
    name: "About",
  },
]);
</script>

<template>
  <header class="header">
    <img src="/assets/logo.svg" alt="snap logo" class="header__logo" />
    <nav>
      <ul class="header__menu">
        <li
          class="header__menu__option-container"
          v-for="option in headerOptions"
          @mouseover="
            ($event) => {
              $event.target
                .closest('.header__menu__option-container')
                .classList.add(`hovered-over`);
            }
          "
          @mouseleave="
            ($event) => {
              $event.target
                .closest('.header__menu__option-container')
                .classList.remove(`hovered-over`);
            }
          "
        >
          <div class="header__menu__option-container__option">
            <div class="header__menu__option-container__option__text">
              {{ option.name }}
            </div>
            <img
              src="/assets/icon-arrow-down.svg"
              alt="arrow"
              class="header__menu__option-container__option__arrow"
              v-if="Object.keys(option).includes(`subOptions`)"
            />
          </div>
          <div
            class="header__menu__option-container__suboptions"
            v-if="Object.keys(option).includes(`subOptions`)"
          >
            <div
              class="header__menu__option-container__suboptions__suboption"
              v-for="subOption in option.subOptions"
            >
              <img
                :src="subOption.icon"
                alt="todo icon"
                class="header__menu__option-container__suboptions__suboption__icon"
                v-if="Object.keys(subOption).includes(`icon`)"
              />
              <div
                class="header__menu__option-container__suboptions__suboption__text"
              >
                {{ subOption.name }}
              </div>
            </div>
          </div>
        </li>
        <li class="header__menu__login">
          <button>Login</button>
        </li>
        <li class="header__menu__register">
          <button>Register</button>
        </li>
      </ul>
    </nav>
    <img
      class="header__menu-opener"
      src="dummy src"
      alt="menu opener"
      @click="triggerMenu()"
    />
    <div class="header__shadow-realm" @click="triggerMenu()"></div>
  </header>
  <main class="main">
    <div class="main__info">
      <h1>Make <span>remote work</span></h1>
      <p>
        Get your team in sync, no matter your location. Streamline processes,
        create team rituals, and watch productivity soar.
      </p>
      <button>Learn more</button>
      <div class="main__info__logos">
        <img src="/assets/client-databiz.svg" alt="databiz logo" />
        <img src="/assets/client-audiophile.svg" alt="audiophile logo" />
        <img src="/assets/client-meet.svg" alt="meet logo" />
        <img src="/assets/client-maker.svg" alt="maker logo" />
      </div>
    </div>
    <img alt="some guy with a laptop" src="dummy src" class="main__giga-img" />
  </main>
</template>

<style scoped></style>
