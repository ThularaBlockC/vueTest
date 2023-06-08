<script>
export default {
  data() {
    return {
      isSticky: false,
      isOpenResponsive: false,
      isResponsive: false,
    };
  },
  mounted() {
    window.addEventListener("scroll", this.handleScroll);
    window.addEventListener("resize", this.handleResize);
    this.handleResize(); // Check responsive mode on initial load
  },
  beforeUnmount() {
    window.removeEventListener("scroll", this.handleScroll);
    window.removeEventListener("resize", this.handleResize);
  },
  methods: {
    toggleMenu() {
      this.isOpenResponsive = !this.isOpenResponsive;
    },
    handleScroll() {
      this.isSticky = window.pageYOffset > 0;
    },
    handleResize() {
      this.isResponsive = window.innerWidth <= 1320;
      if (!this.isResponsive) {
        this.isOpenResponsive = false;
      }
    },
  },
};
</script>

<template>
  <header>
    <nav class="container" :class="{ sticky: isSticky }">
      <div class="branding">
        <img
          src="../assets/vuetify-seeklogo.com.svg"
          alt="Sticky Header Logo"
        />
        <h1>Vue Test Project</h1>
      </div>
      <div class="menu" :class="{ 'nav-menu-open': isOpenResponsive }">
        <div class="hamburger" @click="toggleMenu" v-if="isResponsive">
          <span class="bar"></span>
          <span class="bar"></span>
          <span class="bar"></span>
        </div>
        <ul
          class="nav-routes"
          v-if="!isResponsive || (isResponsive && !isOpenResponsive)"
        >
          <li v-if="!isOpenResponsive"><RouterLink to="/">Home</RouterLink></li>
          <li v-if="!isOpenResponsive">
            <RouterLink to="/about">About</RouterLink>
            <RouterLink to="/contact">Contact</RouterLink>
          </li>
        </ul>
        <ul class="nav-routes-responsive" v-if="isOpenResponsive">
          <li><RouterLink to="/">Home</RouterLink></li>
          <li><RouterLink to="/about">About</RouterLink></li>
          <li><RouterLink to="/contact">Contact</RouterLink></li>
        </ul>
      </div>
    </nav>
  </header>
</template>

<style lang="scss">
header {
  overflow: hidden;
  position: fixed;
  top: 0;
  z-index: 100;
  width: 100%;

  background-image: conic-gradient(
    #553c9a 0%,
    #553c9a 33%,
    #ee4b2b 33%,
    #ee4b2b 66%,
    #1397f6 66%,
    #03eefb 99%
  );

  nav {
    display: flex;
    align-items: center;
    padding: 25px 16px;

    .branding {
      display: flex;
      align-items: center;
      gap: 8px;
      img {
        max-width: 50px;
      }

      h1 {
        background: conic-gradient(
          #eeeb2b 66%,
          #eee12b 66%,
          #ee7c2b 33%,
          #eec72b 66%,
          #ffffff 66%,
          #00c2cb 99%
        );
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        font-size: 30px;
        margin-right: 300px;
      }
    }
    .container {
      align-items: left;
    }

    .menu {
      align-items: end;
    }
    .nav-routes {
      gap: 2px;
      display: flex;
      flex-direction: row;
      align-items: end;
      justify-content: flex-end;
      list-style: none;
      padding: 0;

      li {
        margin-right: 10px;
      }
      a {
        cursor: pointer;
        text-decoration: none;
        font-size: 26px;
        font-weight: 180;
        color: #ffffff;
        padding: 0 5px;
        box-shadow: inset 0 0 0 0 #1cb6eb;
        transition: all 0.6s ease-in-out 0s;
        &:hover {
          box-shadow: inset -400px 0 0 0 #3e2f67;
          color: #ffffff;
        }
      }
    }
  }
}

@media screen and (max-width: 600px) {
  * {
    overflow-y: hidden;
    overflow-x: hidden;
  }

  header {
    nav {
      padding: 5px 6px;

      .branding {
        gap: 5px;
        img {
          max-width: 35px;
        }

        h1 {
          opacity: 0;
          font-size: 10px;
          font-weight: 200;
        }
      }

      .hamburger {
        display: block;
        cursor: pointer;
        margin-right: 10px;
      }

      .hamburger .bar {
        display: block;
        width: 15px;
        height: 2px;
        background-color: #ffffff;
        margin-bottom: 3px;
        transition: all 0.3s;

        &:nth-child(1) {
          transform-origin: 0% 0%;
        }

        &:nth-child(2) {
          transform-origin: 0% 50%;
        }

        &:nth-child(3) {
          transform-origin: 0% 100%;
        }
      }

      .nav-menu-open .hamburger .bar:nth-child(1) {
        transform: rotate(45deg) translate(2px, 2px);
      }

      .nav-menu-open .hamburger .bar:nth-child(2) {
        opacity: 0;
      }

      .nav-menu-open .hamburger .bar:nth-child(3) {
        transform: rotate(-45deg) translate(2px, -2px);
      }

      .nav-routes {
        gap: 2px;

        li {
          display: none;
        }

        a {
          cursor: pointer;
          text-decoration: none;
          font-size: 10px;
          font-weight: 80;
          color: #ffffff;
          padding: 0 0px;
          box-shadow: inset 0 0 0 0 #1cb6eb;
          transition: all 0.6s ease-in-out 0s;
          &:hover {
            box-shadow: inset -400px 0 0 0 #3e2f67;
            color: #ffffff;
          }
        }
      }

      .nav-routes-responsive {
        display: none;
        list-style: none;
        padding: 0;

        li {
          margin-bottom: 10px;
        }

        a {
          cursor: pointer;
          text-decoration: none;
          font-size: 10px;
          font-weight: 80;
          color: #ffffff;
          padding: 0 0px;
          box-shadow: inset 0 0 0 0 #1cb6eb;
          transition: all 0.6s ease-in-out 0s;
          &:hover {
            box-shadow: inset -400px 0 0 0 #3e2f67;
            color: #ffffff;
          }
        }
      }

      .nav-menu-open .nav-routes-responsive {
        position: absolute;
        top: 10%;
        left: 80%;
        width: auto;
        height: auto;
        display: block;
      }
    }
  }
}
</style>
