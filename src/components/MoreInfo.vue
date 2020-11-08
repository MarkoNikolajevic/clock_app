<template>
  <transition name="slide-fade-y">
    <div class='info-grid'>
      <div class='info-col'>
        <div class='info-flex'>
          <h6 class='heading6'>Current timezone</h6>
          <h2 class='heading2'>{{timezone}}</h2>
        </div>
        <div class='info-flex'>
          <h6 class='heading6'>Day of the year</h6>
          <h2 class='heading2'>{{dayOfYear}}</h2>
        </div>
      </div>
      <div class='info-col'>
        <div class='info-flex'>
          <h6 class='heading6'>Day of the week</h6>
          <h2 class='heading2'>{{dayOfWeek}}</h2>
        </div>
        <div class='info-flex'>
          <h6 class='heading6'>Week number</h6>
          <h2 class='heading2'>{{weekNumber}}</h2>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: 'MoreInfo',
  props: {
    timezone: String,
    dayOfYear: Number,
    dayOfWeek: Number,
    weekNumber: Number
  }
}
</script>

<style lang="scss" scoped>
  .info-grid {
    display: grid;
    grid-template-columns: 1fr;
    position: absolute;
    width: 100%;
    bottom: 0;
    padding: 2rem 1.625rem;
    
    @media screen and (min-width: 48rem) {
      padding: 2.5rem 8rem 2.5rem 4rem;
      grid-template-columns: 1fr 1fr;
      gap: 2rem;
    }

    @media screen and (min-width: 85rem) {
      padding: 3.5rem 5.75rem 3.5rem 10.25rem;
    }

    .info-flex {
      display: flex;
      align-items: center;
      justify-content: space-between;

      @media screen and (min-width: 48rem) {
        flex-direction: column;
        align-items: flex-start;
      }
    }
  }
  .daytime {
    background: rgba(255, 255, 255, 0.8);
    color: $darkGray;
  }

  .nighttime {
    color: $white;
    background: rgba(0, 0, 0, 0.75);
  }

  /* animations */
  .slide-fade-y-enter-active {
    transition: all 600ms ease-in-out;
  }
  .slide-fade-y-leave-active {
    transition: all 200ms cubic-bezier(1.0, 0.5, 0.8, 1.0);
  }
  .slide-fade-y-enter, .slide-fade-y-leave-to {
    transform: translateY(100%);
    opacity: 0;
  }
</style>