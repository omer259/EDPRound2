<template>
  <div>
    <section class="pb-0 ratio2_1">
      <div class="container">
        <div class="row partition2">
          <div class="col-md-6" v-for="(item, index) in items" :key="index">
            <nuxt-link :to="{ path: '/collection/leftsidebar/all'}">
              <div class="collection-banner p-center text-center">
                <div class="img-part">
                  <img :src="item.imagepath" class="img-fluid" alt />
                </div>
                <div class="contain-banner">
                  <div>
                    <h4>{{item.subtitle}}</h4>
                    <h2>{{item.title}}</h2>
                  </div>
                </div>
              </div>
            </nuxt-link>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>
<script type="text/javascript">
export default {
  data() {
    return {
      items: [
        {
          imagepath: require('@/assets/images/real/find_a_job_4_resized.jpg'),
          title: 'Find a Job',
          subtitle: 'Your time Your rules'
        },
        {
          imagepath: require('@/assets/images/real/post_a_job_resized.jpg'),
          title: 'Post a Job',
          subtitle: 'Premium service at an affordable price'
        }
      ]
    }
  }
}
</script>
