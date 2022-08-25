<template>
  <section class="container mt-5">
    <div class="columns is-multiline">
      <div class="column is-6" v-for="univ in universities">
        <div class="card">
          <div class="card-content">
            <div class="content">
              <div class="d-flex justify-content-between">
                <div><span class="tag is-primary">Name </span></div>
                <div>{{univ.name}}</div>
              </div>
              <div class="d-flex justify-content-between mt-4">
                <div><span class="tag is-primary">web pages </span></div>
                <div>{{univ.web_pages}}</div>
              </div>
              <div class="d-flex justify-content-between mt-3">
                <div><span class="tag is-primary">Country </span></div>
                <div>{{univ.country}}</div>
              </div>
               <div class="d-flex justify-content-between mt-3">
                <div><span class="tag is-primary">Code </span></div>
                <div>{{univ.alpha_two_code}}</div>
              </div>
            </div>
          </div>
          <div class="card-footer">
            <div class="d-flex justify-content-between">
              <span class="tag is-dark">@CopyRight Esmail</span>
            </div>
          </div>
        </div>
      </div>

    </div>
  </section>
</template>

<script>
  export default {
    name: 'IndexPage',
    data: () => ({
      universities: [],
    }),
    mounted() {
      this.getData();
    },
    methods: {

      getData() {
        const api = `http://universities.hipolabs.com/search?country=United+States`;
        fetch(api)
          .then(response => {
            if (response.ok) {
              return response.json();
            }
          }).then(data => {
            if (data) {
              this.universities = data;
              console.log("data");
            }
          })
      }
    }
  }

</script>
