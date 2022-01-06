<template>
  <div id="observer-root">
    <div id="block1">
      <div id="text1">
        Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo
        ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis
        dis parturient montes, nascetur ridiculus mus. Donec quam felis,
        ultricies nec, pellentesque eu, pretium quis, sem. Nulla consequat massa
        quis enim. Donec pede justo, fringilla vel, aliquet nec, vulputate eget,
        arcu. In enim justo, rhoncus ut, imperdiet a, venenatis vitae, justo.
        Nullam dictum felis eu pede mollis pretium. Integer tincidunt. Cras
        dapibus. Vivamus elementum semper nisi.
      </div>
    </div>

    <div id="block2">
      <img alt="Vue logo" src="../assets/logo.png" />
      <div id="text2">
        Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo
        ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis
        dis parturient montes, nascetur ridiculus mus. Donec quam felis,
        ultricies nec, pellentesque eu, pretium quis, sem. Nulla consequat massa
        quis enim. Donec pede justo, fringilla vel, aliquet nec, vulputate eget,
        arcu. In enim justo, rhoncußs ut, imperdiet a, venenatis vitae, justo.
        Nullam dictum felis eu pede mollis pretium. Integer tincidunt. Cras
        dapibus. Vivamus elementum semper nisi.
      </div>
    </div>

    <div id="block3">
      <img alt="Vue logo" src="../assets/logo.png" />
      <div id="text3">
        Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo
        ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis
        dis parturient montes, nascetur ridiculus mus. Donec quam felis,
        ultricies nec, pellentesque eu, pretium quis, sem. Nulla consequat massa
        quis enim. Donec pede justo, fringilla vel, aliquet nec, vulputate eget,
        arcu. In enim justo, rhoncußs ut, imperdiet a, venenatis vitae, justo.
        Nullam dictum felis eu pede mollis pretium. Integer tincidunt. Cras
        dapibus. Vivamus elementum semper nisi.
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TestsBlocks",

  data() {
    return {};
  },

  mounted() {
    let options = {
      root: null, //document.querySelector('observer-root'), //viewport
      rootMargin: "0px",
      threshold: 0.5,
    };

    let observer = new IntersectionObserver(
      this.onElementObserved.bind(this),
      options
    );

    let target = this.$el.querySelector("#text2");
    observer.observe(target);
  },

  methods: {
    onElementObserved(entries) {
      //console.log(entries);
      entries.forEach(({ target, isIntersecting }) => {
        console.log(target);
        if (isIntersecting) {
          return target.classList.add("in-sight");
        }
      });
    },
  },
};
</script>

<style lang="scss" scoped>
#observer-root {
  height: 100vh;
  overflow: scroll;
}
#block1 {
  height: 100vh;
  background-color: bisque;
  padding: 2em;
}
#block2 {
  background-color: rgb(138, 187, 209);
  height: 100vh;
  padding: 2em;
}
#text1 {
    
  font-size: 1em;
}

#text2 {
  font-size: 1.5em;
  opacity: 0;
}

#text2.in-sight {
  animation: fade-in-move-up 1s 1;
  opacity: 1;
}

@keyframes fade-in-move-up {
  0% {
    opacity: 0;
    transform: translateY(3rem);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>