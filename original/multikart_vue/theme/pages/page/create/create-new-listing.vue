<template>
<div>
    <Header />
    <Breadcrumbs title="New Listing" />
    <div class="title1 section-t-space">
      <h2 class="title-inner1">{{title}}</h2>
      <h4>{{subtitle}}</h4>
    </div>
    <section class="section-b-space p-t-0 ratio_asos">
      <div class="container">
        <div class="row">
          <div class="col-md-12">
            <br>
            <div class="slide-6 no-arrow">
              <div v-swiper:mySwiper="swiperOption">
                <div class="swiper-wrapper">
                  <div class="swiper-slide" v-for="(item, index) in items" :key="index">
                    <div>
                      <div class="logo-block text-center">
                        <a href="/page/create/create-details-page">
                          <img :src="item.imagepath" alt />
                        </a>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
            <p align = "center"><br>{{subtitle1Desc}}</p>
          </div>
        </div>
      </div>
    </section>
    <div class="title1">
      <h4>{{subtitle2}}</h4>
    </div>
    <section class="section-b-space p-t-0 ratio_asos">
      <div class="container">
        <div class="row">
          <div class="col-md-12">
            <p align = "center">{{subtitle2Desc}}</p>
            <button align="right" type="submit" class="btn btn-solid btn-center" id="create-custom">Customize</button>
          </div>
        </div>
      </div>
    </section>
    <Footer />
</div>
</template>

<script type="text/javascript">
import { mapState } from 'vuex'
import Header from '../../../components/header/header1'
import Footer from '../../../components/footer/footer1'
import Breadcrumbs from '../../../components/widgets/breadcrumbs'
export default {
  components: {
    Header,
    Footer,
    Breadcrumbs
  },
  data() {
    return {
      products: [],
      category: [],
      title: 'Create new Listing',
      subtitle: 'Select an existing category to get started quickly!',
      subtitle1Desc: 'Get your jobs posted or services listed in mere seconds.',
      subtitle2: 'Other Options',
      subtitle2Desc: 'Want to create a more customized listing? Get started by selecting the customize button below.',
      swiperOption: {
        slidesPerView: 6,
        freeMode: true,
        breakpoints: {
          1199: {
            slidesPerView: 4
          },
          768: {
            slidesPerView: 3
          },
          420: {
            slidesPerView: 2
          }
        }
      },
      items: [
        {
          imagepath: require('@/assets/images/logos/Cleaning.jpg')
        },
        {
          imagepath: require('@/assets/images/logos/Handyman.png')
        },
        {
          imagepath: require('@/assets/images/logos/Tutoring.jpg')
        },
        {
          imagepath: require('@/assets/images/logos/lawncare.png')
        },
        {
          imagepath: require('@/assets/images/logos/Cleaning.jpg')
        },
        {
          imagepath: require('@/assets/images/logos/Handyman.png')
        },
        {
          imagepath: require('@/assets/images/logos/Tutoring.jpg')
        },
        {
          imagepath: require('@/assets/images/logos/lawncare.png')
        }
      ]
    }
  },
  computed: {
    ...mapState({
      productslist: state => state.products.productslist
    })
  },
  mounted() {
    this.productsArray()
  },
  methods: {
    productsArray: function () {
      this.productslist.map((item) => {
        if (item.type === 'fashion') {
          this.products.push(item)
          item.collection.map((i) => {
            const index = this.category.indexOf(i)
            if (index === -1) this.category.push(i)
          })
        }
      })
    },
    getCategoryProduct(collection) {
      return this.products.filter((item) => {
        if (item.collection.find(i => i === collection)) {
          return item
        }
      })
    },
    alert(item) {
      this.dismissCountDown = item
    }
  }
}
</script>
