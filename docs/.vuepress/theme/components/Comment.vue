<template>
    <v-card>
        <v-card-title>
            <div id="gitalk-container" class="comment"></div>
        </v-card-title>
    </v-card>
</template>
<script>

  export default {
    mounted(){
      this.haveGitalk();
    },
    methods: {
      haveGitalk(){
        if (typeof Gitalk !== 'undefined' && Gitalk instanceof Function) {
          this.renderGitalk();
        } else {
          setTimeout(() => {this.haveGitalk()}, 1000)
        }
      },
      renderGitalk(){
        if (typeof Gitalk !== 'undefined' && Gitalk instanceof Function) {
          const gitalk = new Gitalk({
            clientID: '6ac606b7bad30bff534c',
            clientSecret: 'cf218bccc6b17b1feaee02b406d0c1f021aaa5e7',
            repo: 'blog',
            owner: 'iofu728',
            admin: ['iofu728'],
            id: 'comment',
            distractionFreeMode: false,
            language: 'zh-CN',
          })
          try {
            document && gitalk.render("gitalk-container");
          } catch (e) {
            console.error(e.message)
          }
        }
      }
    }

  }
</script>
<style lang="stylus">
  .comment
    padding 1rem
    margin 0 auto

</style>
