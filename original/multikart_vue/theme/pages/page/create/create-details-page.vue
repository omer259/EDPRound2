<template>
<div>
    <Header />
    <Breadcrumbs title="New Listing" />
    <div class="title1 section-t-space">
      <h4>{{subtitle}}</h4>
      <h2 class="title-inner1">{{title}}</h2>
    </div>
    <section class="section-b-space p-t-0 ratio_asos">
      <div class="container">
        <div class="row">
          <p>Select one of the options below to create a quick posting!<br></p>
          <p>Otherwise please create a new listing from scratch here: </p>
        </div>
      </div>
    </section>
    <Footer />
</div>
</template>

<script>
import { mapState } from 'vuex'
import Header from '../../../components/header/header1'
import Footer from '../../../components/footer/footer1'
export default {
  components: {
    Header,
    Footer
  },
  data() {
    return {
      products: [],
      category: [],
      title: 'select category',
      subtitle: 'quick create',
      description:
        'Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industrys standard dummy text ever since the 1500s.'
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
    },
  }
}
</script>
