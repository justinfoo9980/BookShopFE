<template>
  <vue-slick ref="slick" :options="option">
    <slot />
  </vue-slick>
</template>
<script>
import VueSlick from 'vue-slick'
import { mapGetters } from 'vuex'
export default {
  name: 'Slick',
  components: {
    VueSlick
  },
  watch: {
    'rtl': function () {
      this.reInit()
    }
  },
  computed: {
    ...mapGetters({
      rtl: 'Setting/rtlModeState'
    })
  },
  props: {

    option: {
      type: Object,
      default: () => {
        return {
          centerMode: false,
          centerPadding: '60px',
          slidesToShow: 2,
          slidesToScroll: 1,
          focusOnSelect: true,
          responsive: [
            {
              breakpoint: 992,
              settings: {
                arrows: false,
                centerMode: true,
                centerPadding: '30',
                slidesToShow: 1
              }
            },
            {
              breakpoint: 480,
              settings: {
                arrows: false,
                centerMode: true,
                centerPadding: '15',
                slidesToShow: 1
              }
            }
          ],
          nextArrow: '<a href="#" class="ri-arrow-left-s-line left"></a>',
          prevArrow: '<a href="#" class="ri-arrow-right-s-line right"></a>'
        }
      }
    }
  },
  methods: {
    reInit () {
      this.$nextTick(() => {
        this.$refs.slick.reSlick()
      })
    }
  }
}
</script>
