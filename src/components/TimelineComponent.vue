<template>
  <div class="timeline-component page__line">
      <ul>
          <li v-for="item in items" :key="item.id">
              <router-link :to="{ name: item.route }" class="timeline-component__link">
                <div class="timeline-component__name"
                     :class="{'timeline-component__name-active': isActive(item.route)}">
                  {{ item.name }}
                </div>

                <div class="timeline-component__button"
                     :class="{'timeline-component__button-active': isActive(item.route)}">
                </div>
              </router-link>
          </li>
      </ul>
  </div>
</template>

<script>
export default {
  name: 'timeline-component',
  data () {
    return {
      items: [
        {
          name: 'sept.',
          route: 'september'
        },
        {
          name: 'oct.',
          route: 'october'
        },
        {
          name: 'nov.',
          route: 'november'
        },
        {
          name: 'dec.',
          route: 'december'
        },
        {
          name: 'jan.',
          route: 'january'
        },
        {
          name: 'feb.',
          route: 'february'
        },
        {
          name: 'mar.',
          route: 'march'
        },
        {
          name: 'apr.',
          route: 'april'
        }
      ]
    }
  },
  methods: {
    isActive (routeName) {
      return this.$route.name === routeName
    }
  },
  mounted () {
    this.currentRoute = this.$router.currentRoute.name
  }
}
</script>

<style lang="scss">
  body.chatbot .timeline-component__button {
    background-color: $blue;
    transition: all .8s ease;
  }

  .timeline-component {
    z-index: 3;
    position: absolute;
    left: 50%;
    bottom: 4rem;
    transform: translateX(-50%);
    height: 5.5rem;
    transition: all .3s ease;
    opacity: .5;

    &:hover {
      opacity: 1;
    }

    & a.timeline-component__link {
      &:hover {

        & .timeline-component__button {
          background-color: $white;
        }

        & .timeline-component__name {
          opacity: 1;
        }
      }
    }

    &__name {
      opacity: 0;
      transition: all .3s ease;

      &-active {
        opacity: 1;
      }
    }

    &__button {
      content: '';
      position: absolute;
      left: -1.7rem;
      bottom: -1.6rem;
      width: 1.5rem;
      height: 1.5rem;
      border: 0.2rem solid $white;
      border-radius: 50%;
      background-color: $main-color;
      transition: all .3s ease;
      cursor: pointer;

      &-active {
        background-color: $white;
      }
    }

    &.page__line {
      &::before {
        width: 100%;
        margin-top: 1.55rem;
      }
    }

    ul {
      display: flex;
      justify-content: space-around;
      margin: 0;
      padding: 0;
      width: 80vw;

      li {
        width: 4rem;
        list-style-type: none;
        transform: rotate(-45deg);

        a {
          @include fontSize(16);
          color: $white;
        }
      }
    }
  }
</style>
