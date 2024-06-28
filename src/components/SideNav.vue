<scripit setup>

</scripit>

<template>
  <nav class="navbar">
    <ul class="navbar-nav">
      <li class="logo">
        <router-link to="/" class="nav-link">
          <span class="link-text logo-text">Arbiter</span>
          <svg class="fa-primary" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 512">
            <!--!Font Awesome Free 6.5.2 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2024 Fonticons, Inc.-->
            <path
              d="M117.9 62.4c-16.8-5.6-25.8-23.7-20.2-40.5s23.7-25.8 40.5-20.2l113 37.7C265 15.8 290.7 0 320 0c44.2 0 80 35.8 80 80c0 3-.2 5.9-.5 8.8l122.6 40.9c16.8 5.6 25.8 23.7 20.2 40.5s-23.7 25.8-40.5 20.2L366.4 145.2c-4.5 3.2-9.3 5.9-14.4 8.2V480c0 17.7-14.3 32-32 32H128c-17.7 0-32-14.3-32-32s14.3-32 32-32H288V153.3c-21-9.2-37.2-27-44.2-49l-125.9-42zM200.4 288L128 163.8 55.6 288H200.4zM128 384C65.1 384 12.8 350 2 305.1c-2.6-11 1-22.3 6.7-32.1l95.2-163.2c5-8.6 14.2-13.8 24.1-13.8s19.1 5.3 24.1 13.8l95.2 163.2c5.7 9.8 9.3 21.1 6.7 32.1C243.2 350 190.9 384 128 384zm382.8-92.2L438.4 416H583.3L510.8 291.8zm126 141.3C626 478 573.7 512 510.8 512s-115.2-34-126-78.9c-2.6-11 1-22.3 6.7-32.1l95.2-163.2c5-8.6 14.2-13.8 24.1-13.8s19.1 5.3 24.1 13.8l95.2 163.2c5.7 9.8 9.3 21.1 6.7 32.1z"
            />
          </svg>
        </router-link>
      </li>
      <template v-if="loggedIn">
        <li class="nav-item">
          <router-link to="/" class="nav-link">
            <svg
              aria-hidden="true"
              focusable="false"
              data-prefix="fas"
              data-icon="home"
              class="svg-inline--fa fa-home fa-w-18"
              role="img"
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 576 512"
            >
              <path
                fill="#ff7eee"
                class="fa-primary"
                d="M280.37 148.26L96 300.11V464a16 16 0 0 0 16 16l112.06-.29a16 16 0 0 0 15.92-16V368a16 16 0 0 1 16-16h64a16 16 0 0 1 16 16v95.64a16 16 0 0 0 16 16.05L464 480a16 16 0 0 0 16-16V300L295.67 148.26a12.19 12.19 0 0 0-15.3 0zM571.6 251.47L488 182.56V44.05a12 12 0 0 0-12-12h-56a12 12 0 0 0-12 12v72.61L318.47 43a48 48 0 0 0-61 0L4.34 251.47a12 12 0 0 0-1.6 16.9l25.5 31A12 12 0 0 0 45.15 301l235.22-193.74a12.19 12.19 0 0 1 15.3 0L530.9 301a12 12 0 0 0 16.9-1.6l25.5-31a12 12 0 0 0-1.7-16.93z"
              ></path>
            </svg>
            <span class="link-text">Home</span>
          </router-link>
        </li>
        <li class="nav-item">
          <router-link to="/profile" class="nav-link">
            <svg
              aria-hidden="true"
              focusable="false"
              data-prefix="fas"
              data-icon="cogs"
              class="svg-inline--fa fa-cogs fa-w-20"
              role="img"
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 640 512"
            >
              <path
                fill="currentColor"
                class="fa-primary"
                d="M224 256c70.7 0 128-57.31 128-128s-57.3-128-128-128C153.3 0 96 57.31 96 128S153.3 256 224 256zM274.7 304H173.3C77.61 304 0 381.6 0 477.3c0 19.14 15.52 34.67 34.66 34.67h378.7C432.5 512 448 496.5 448 477.3C448 381.6 370.4 304 274.7 304z"
              />
            </svg>
            <span class="link-text">Profile</span>
          </router-link>
        </li>
      </template>
      <li class="nav-item">
        <router-link to="/rankings" class="nav-link">
          <svg xmlns="http://www.w3.org/2000/svg" class="fa-primary" viewBox="0 0 448 512">
            <!--!Font Awesome Free 6.5.2 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2024 Fonticons, Inc.-->
            <path
              d="M304 128a80 80 0 1 0 -160 0 80 80 0 1 0 160 0zM96 128a128 128 0 1 1 256 0A128 128 0 1 1 96 128zM49.3 464H398.7c-8.9-63.3-63.3-112-129-112H178.3c-65.7 0-120.1 48.7-129 112zM0 482.3C0 383.8 79.8 304 178.3 304h91.4C368.2 304 448 383.8 448 482.3c0 16.4-13.3 29.7-29.7 29.7H29.7C13.3 512 0 498.7 0 482.3z"
            />
          </svg>
          <span class="link-text">Teams</span>
        </router-link>
        <div v-if="tooltip === 'teams'" class="arrow"></div>
      </li>
      <li class="nav-item">
        <router-link to="/about" class="nav-link">
          <svg
            aria-hidden="true"
            focusable="false"
            data-prefix="fas"
            data-icon="info-circle"
            class="svg-inline--fa fa-info-circle fa-w-16"
            role="img"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 512 512"
          >
            <path
              fill="currentColor"
              class="fa-primary"
              d="M256 8C119.043 8 8 119.083 8 256c0 136.997 111.043 248 248 248s248-111.003 248-248C504 119.083 392.957 8 256 8zm0 110c23.196 0 42 18.804 42 42s-18.804 42-42 42-42-18.804-42-42 18.804-42 42-42zm56 254c0 6.627-5.373 12-12 12h-88c-6.627 0-12-5.373-12-12v-24c0-6.627 5.373-12 12-12h12v-64h-12c-6.627 0-12-5.373-12-12v-24c0-6.627 5.373-12 12-12h64c6.627 0 12 5.373 12 12v100h12c6.627 0 12 5.373 12 12v24z"
            ></path>
          </svg>
          <span class="link-text">About</span>
        </router-link>
      </li>
      <template v-if="loggedIn">
        <li v-if="loggedIn" class="nav-item bottom">
          <div @click="logout" class="nav-link">
            <svg
              aria-hidden="true"
              focusable="false"
              data-prefix="fas"
              data-icon="sign-out-alt"
              class="svg-inline--fa fa-sign-out-alt fa-w-16"
              role="img"
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 512 512"
            >
              <path
                fill="currentColor"
                class="fa-primary"
                d="M497 273L329 441c-15 15-41 4.5-41-17v-96H152c-13.3 0-24-10.7-24-24v-96c0-13.3 10.7-24 24-24h136V88c0-21.4 25.9-32 41-17l168 168c9.3 9.4 9.3 24.6 0 34zM192 436v-40c0-6.6-5.4-12-12-12H96c-17.7 0-32-14.3-32-32V160c0-17.7 14.3-32 32-32h84c6.6 0 12-5.4 12-12V76c0-6.6-5.4-12-12-12H96c-53 0-96 43-96 96v192c0 53 43 96 96 96h84c6.6 0 12-5.4 12-12z"
              ></path>
            </svg>
            <span class="link-text">Logout</span>
          </div>
        </li>
      </template>
      <template v-else>
        <li class="nav-item bottom" @click="signIn">
          <div class="nav-link">
            <svg
              aria-hidden="true"
              focusable="false"
              data-prefix="fab"
              data-icon="twitter"
              class="svg-inline--fa fa-twitter fa-w-16"
              role="img"
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 512 512"
            >
              <path
                fill="currentColor"
                class="fa-primary"
                d="M459.37 151.716c.325 4.548.325 9.097.325 13.645 0 138.72-105.583 298.558-298.558 298.558-59.452 0-114.68-17.219-161.137-47.106 8.447.974 16.568 1.299 25.34 1.299 49.055 0 94.213-16.568 130.274-44.832-46.132-.975-84.792-31.188-98.112-72.772 6.498.974 12.995 1.624 19.818 1.624 9.421 0 18.843-1.3 27.614-3.573-48.081-9.747-84.143-51.98-84.143-102.985v-1.299c13.969 7.797 30.214 12.67 47.431 13.319-28.264-18.843-46.781-51.005-46.781-87.391 0-19.492 5.197-37.36 14.294-52.954 51.655 63.675 129.3 105.258 216.365 109.807-1.624-7.797-2.599-15.918-2.599-24.04 0-57.828 46.782-104.934 104.934-104.934 30.213 0 57.502 12.67 76.67 33.137 23.715-4.548 46.456-13.32 66.599-25.34-7.798 24.366-24.366 44.833-46.132 57.827 21.117-2.273 41.584-8.122 60.426-16.243-14.292 20.791-32.161 39.308-52.628 54.253z"
              ></path>
            </svg>
            <span class="link-text">Login</span>
          </div>
        </li>
      </template>
    </ul>
  </nav>
</template>

<style lang="scss" scoped>
.navbar {
  position: fixed;
  background-color: #23232e;
  transition: width 600ms ease;
  // overflow: hidden;
  z-index: 100;

  .navbar-nav {
    list-style: none;
    padding: 0 !important;
    margin: 0 !important;
    display: flex;
    flex-direction: column;
    align-items: center;
    height: 100%;

    .logo {
      font-weight: bold;
      text-transform: uppercase;
      margin-bottom: 1rem;
      text-align: center;
      color: #ececec;
      background: #141418;
      font-size: 1.5rem;
      letter-spacing: 0.3ch;
      width: 100%;

      svg {
        transform: rotate(0deg);
        transition: 600ms;
      }
    }
  }

  .nav-item {
    width: 100%;
    position: relative;
    &.bottom {
      margin-top: auto;
    }
  }

  .arrow {
    position: absolute;
    top: 27px;
    right: -60px;
    content: '';
    background: #ff7eee;
    width: 60px;
    height: 26px;
    animation: arrowMove 1s infinite;

    &::before {
      height: 20px;
      color: #ff7eee;
      border-right: 13px solid;
      border-top: 13px solid transparent;
      border-bottom: 13px solid transparent;
      display: inline-block;
      content: '';
      position: absolute;
      left: -13px;
    }
  }
}

.nav-link {
  display: flex;
  align-items: center;
  height: 5rem;
  color: #b6b6b6;
  text-decoration: none;
  filter: grayscale(100%) opacity(0.7);
  transition: 600ms;
  cursor: pointer;

  &:hover {
    filter: grayscale(0%) opacity(1);
    background: #141418;
    color: #ececec;
  }

  svg {
    width: 2rem;
    min-width: 2rem;
    margin: 0 1.5rem;
    color: #ff7eee;
  }
}

.link-text {
  display: none;
  margin-left: 1rem;
}

.fa-primary {
  path {
    color: #ff7eee;
    fill: #ff7eee;
    transition: 600ms;
  }
}

.logo-text {
  display: inline;
  position: absolute;
  left: -999px;
  transition: 600ms;
}

.navbar:hover .logo svg {
  transform: scale(-1, 1);
}

/* Small screens */
@media only screen and (max-width: 600px) {
  .navbar {
    bottom: 0;
    width: 100vw;
    height: 5rem;
  }

  .logo {
    display: none;
  }

  .navbar-nav {
    flex-direction: row;
  }

  .nav-item {
    width: calc(100vw / 5);
  }

  .nav-link {
    justify-content: center;
  }

  main {
    margin: 0;
  }
}

/* Large screens */
@media only screen and (min-width: 600px) {
  .navbar {
    top: 0;
    width: 5rem;
    height: 100vh;
  }

  .navbar:hover {
    width: 16rem;
  }

  .navbar:hover .link-text {
    display: inline;
  }

  .navbar:hover .logo svg {
    margin-left: 11rem;
  }

  .navbar:hover .logo-text {
    left: 0px;
  }
}

// keyframes
@-webkit-keyframes arrowMove {
  0% {
    right: -103px;
  }
  50% {
    right: -73px;
  }
  100% {
    right: -103px;
  }
}
</style>
