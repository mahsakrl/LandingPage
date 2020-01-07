<template>
  <div class="home">
    <div class="whitish-bg">
      <div class="menu">
        <div class="menu-logo">
          <img style="width:80px;height:30px" src="../assets/images/logo.svg" />
          <ul class="menu-item">
            <li>Features</li>
            <li>Pricing</li>
            <li>Resources</li>
          </ul>
        </div>
        <div class="login">
          <button class="login-btn">login</button>
          <button>sign up</button>
          <i class="material-icons mobile" @click="openNav()">menu</i>
          <div id="myNav" class="overlay mobile">
            <a class="closebtn mobile" @click="closeNav()">&times;</a>
            <div class="overlay-content mobile" @click="closeNav()">
              <a class="mobile" href="#">Feature</a>
              <a class="mobile" href="#">Pricing</a>
              <a class="mobile" href="#">Resources</a>
            </div>
          </div>
        </div>
      </div>
      <div class="header">
        <div class="header-content">
          <h1>More than just shorter links</h1>
          <p>
            Build your brand’s recognition and get detailed insights on how
            your links are performing.
          </p>
          <button>Get Started</button>
        </div>
        <div class="header-img">
          <img src="../assets/images/illustration-working.svg" />
        </div>
      </div>
    </div>
    <div class="search-container">
      <div class="search">
        <div>
          <input
            placeholder="shorten a link here..."
            v-model="url"
            v-on:keyup="validateLinkAddress"
          />
          <button @click="shorten()" class="buttonload">
            <i class="fa fa-refresh fa-spin" v-if="loading"></i>shorten it!
          </button>
        </div>
        <div v-if="error" class="error">{{ errMSG }}please add alink</div>
      </div>
    </div>
    <div class="greyish-bg">
      <div class="shorten-list">
        <div v-for="(item, index) in result" :key="index" class="search-result">
          <div class="result-link">{{ item }}</div>
          <div class="result-btns">
            <div>short link</div>
            <div>
              <button class="copy-btn" v-if="!copied">copy</button>
              <button class="copied-btn" v-if="copied">copied</button>
            </div>
          </div>
        </div>
      </div>
      <div class="statics">
        <h2>Advanced statics</h2>
        <p>
          Track how your links are performing across the web with our advanced
          statistics dashboard.
        </p>
      </div>
      <div class="cards">
        <Card
          class="card"
          title="Brand Recognitaion"
          subTitle="Boost your links today Get Started Features Link Shortening Branded Links Analytics Resources Blog Developers Support Company About Our Team Careers Contact"
          image="../assets/images/icon-brand-recognition.svg"
        />
        <hr />
        <div class="vl" />
        <Card
          class="card card2"
          title="Detailed Records"
          subTitle="Gain insights into who is clicking your links. Knowing when and where people engage with your content helps inform better decisions."
          image="../assets/images/icon-brand-recognition.svg"
        />
        <hr />
        <div class="vl" />

        <Card
          class="card card3"
          title="Fully Customizable"
          subTitle="Improve brand awareness and content discoverability through customizable links, supercharging audience engagement."
          image="../assets/images/icon-brand-recognition.svg"
        />
        <hr />
      </div>
    </div>
    <div class="boost">
      <div style="margin:40px">Boosts your link today</div>
      <button>Get Started</button>
    </div>
    <div class="footer">
      <div class="logo">
        <svg xmlns="http://www.w3.org/2000/svg" width="121" height="33">
          <path
            fill="white"
            d="M16.715 7.932c-.068-.09-.306-.26-.714-.51s-.918-.51-1.53-.782-1.281-.51-2.006-.714a8.005 8.005 0 00-2.176-.306c-1.995 0-2.992.669-2.992 2.006 0 .408.107.748.323 1.02.215.272.532.516.952.731.419.215.946.414 1.58.595l1.406.393.805.219c1.156.317 2.198.663 3.128 1.037.929.374 1.717.839 2.363 1.394a5.647 5.647 0 011.496 2.023c.35.793.527 1.745.527 2.856 0 1.36-.255 2.51-.765 3.451-.51.94-1.185 1.7-2.023 2.278-.84.578-1.802.997-2.89 1.258-1.088.26-2.21.391-3.366.391a19.68 19.68 0 01-5.44-.799c-.884-.26-1.74-.572-2.567-.935A14.358 14.358 0 01.53 22.28l2.448-4.862c.09.113.385.329.884.646.498.317 1.116.635 1.853.952.736.317 1.558.6 2.465.85.906.25 1.824.374 2.754.374 1.972 0 2.958-.6 2.958-1.802 0-.453-.148-.827-.442-1.122-.295-.295-.703-.561-1.224-.799a12.455 12.455 0 00-1.504-.56l-1.702-.495-.976-.288c-1.111-.34-2.074-.708-2.89-1.105-.816-.397-1.49-.856-2.023-1.377a5.003 5.003 0 01-1.19-1.802c-.261-.68-.391-1.473-.391-2.38 0-1.27.238-2.391.714-3.366a7.266 7.266 0 011.938-2.465 8.435 8.435 0 012.839-1.513c1.076-.34 2.215-.51 3.417-.51.838 0 1.666.08 2.482.238.816.159 1.598.363 2.346.612.748.25 1.445.533 2.09.85.647.317 1.242.635 1.786.952l-2.448 4.624zM40.139 25h-5.44V14.97c0-1.156-.227-2.006-.68-2.55-.454-.544-1.077-.816-1.87-.816-.318 0-.663.074-1.037.221a4.173 4.173 0 00-1.088.646 5.827 5.827 0 00-.97 1.003 4.4 4.4 0 00-.68 1.292V25h-5.44V.18h5.44v9.962a6.786 6.786 0 012.602-2.465c1.076-.578 2.26-.867 3.553-.867 1.201 0 2.17.21 2.907.629.736.42 1.303.952 1.7 1.598.396.646.663 1.371.799 2.176.136.805.204 1.592.204 2.363V25zm12.34.34c-1.519 0-2.873-.25-4.063-.748-1.19-.499-2.193-1.173-3.01-2.023a8.54 8.54 0 01-1.852-2.958 9.97 9.97 0 01-.63-3.519c0-1.224.21-2.397.63-3.519a8.54 8.54 0 011.853-2.958c.816-.85 1.819-1.53 3.009-2.04s2.544-.765 4.063-.765c1.519 0 2.867.255 4.046.765 1.179.51 2.176 1.19 2.992 2.04a8.754 8.754 0 011.87 2.958 9.736 9.736 0 01.646 3.519 9.97 9.97 0 01-.63 3.519 8.54 8.54 0 01-1.852 2.958c-.816.85-1.82 1.524-3.01 2.023-1.19.499-2.543.748-4.062.748zM48.5 16.092c0 1.405.374 2.533 1.122 3.383.748.85 1.7 1.275 2.856 1.275a3.59 3.59 0 001.564-.34c.476-.227.89-.544 1.24-.952a4.57 4.57 0 00.834-1.479 5.632 5.632 0 00.306-1.887c0-1.405-.374-2.533-1.122-3.383-.748-.85-1.689-1.275-2.822-1.275a3.702 3.702 0 00-2.84 1.292 4.57 4.57 0 00-.832 1.479 5.632 5.632 0 00-.306 1.887zm27.776-4.284c-1.315.023-2.505.238-3.57.646-1.065.408-1.836 1.02-2.312 1.836V25h-5.44V7.15h4.998v3.604c.612-1.201 1.4-2.142 2.363-2.822.963-.68 1.989-1.031 3.077-1.054h.544c.113 0 .227.011.34.034v4.896zm14.074 12.24a21.71 21.71 0 01-2.567.884c-.963.272-1.932.408-2.907.408-.68 0-1.32-.085-1.92-.255a4.286 4.286 0 01-1.582-.816c-.453-.374-.81-.867-1.07-1.479-.262-.612-.392-1.349-.392-2.21v-9.316h-2.278V7.15h2.278V1.472h5.44V7.15h3.638v4.114h-3.638v7.446c0 .59.147 1.014.442 1.275.295.26.669.391 1.122.391.408 0 .827-.068 1.258-.204.43-.136.805-.283 1.122-.442l1.054 4.318zM92.627.18h5.44v18.462c0 1.36.578 2.04 1.734 2.04.272 0 .572-.04.901-.119.329-.08.63-.198.901-.357l.714 4.08c-.68.317-1.462.567-2.346.748-.884.181-1.711.272-2.482.272-1.564 0-2.765-.408-3.604-1.224-.839-.816-1.258-1.995-1.258-3.536V.18zm11.456 27.506c.454.159.879.272 1.275.34a6.4 6.4 0 001.071.102c.658 0 1.168-.227 1.53-.68.363-.453.692-1.27.986-2.448l-6.8-17.85h5.61l4.148 13.192 3.57-13.192h5.1l-6.8 20.74a7.106 7.106 0 01-2.55 3.587c-1.224.918-2.674 1.377-4.352 1.377a8.17 8.17 0 01-1.377-.119 7.516 7.516 0 01-1.41-.391v-4.658z"
          />
        </svg>
      </div>
      <div class="list">
        <ul>
          <li class="list-header">Features Link</li>
          <li>Link Shortening</li>
          <li>Branded Links</li>
          <li>Analytics</li>
        </ul>
        <ul>
          <li class="list-header">Resources</li>
          <li>Blog</li>
          <li>Developers</li>
          <li>Support</li>
        </ul>
        <ul>
          <li class="list-header">Company</li>
          <li>About</li>
          <li>Careers</li>
          <li>Contact</li>
          <li>Our Team</li>
        </ul>
      </div>
      <div class="social">
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24">
          <path
            d="M22.675 0H1.325C.593 0 0 .593 0 1.325v21.351C0 23.407.593 24 1.325 24H12.82v-9.294H9.692v-3.622h3.128V8.413c0-3.1 1.893-4.788 4.659-4.788 1.325 0 2.463.099 2.795.143v3.24l-1.918.001c-1.504 0-1.795.715-1.795 1.763v2.313h3.587l-.467 3.622h-3.12V24h6.116c.73 0 1.323-.593 1.323-1.325V1.325C24 .593 23.407 0 22.675 0z"
          />
        </svg>
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="20">
          <path
            d="M24 2.557a9.83 9.83 0 01-2.828.775A4.932 4.932 0 0023.337.608a9.864 9.864 0 01-3.127 1.195A4.916 4.916 0 0016.616.248c-3.179 0-5.515 2.966-4.797 6.045A13.978 13.978 0 011.671 1.149a4.93 4.93 0 001.523 6.574 4.903 4.903 0 01-2.229-.616c-.054 2.281 1.581 4.415 3.949 4.89a4.935 4.935 0 01-2.224.084 4.928 4.928 0 004.6 3.419A9.9 9.9 0 010 17.54a13.94 13.94 0 007.548 2.212c9.142 0 14.307-7.721 13.995-14.646A10.025 10.025 0 0024 2.557z"
          />
        </svg>
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24">
          <path
            d="M12 0C5.373 0 0 5.372 0 12c0 5.084 3.163 9.426 7.627 11.174-.105-.949-.2-2.405.042-3.441.218-.937 1.407-5.965 1.407-5.965s-.359-.719-.359-1.782c0-1.668.967-2.914 2.171-2.914 1.023 0 1.518.769 1.518 1.69 0 1.029-.655 2.568-.994 3.995-.283 1.194.599 2.169 1.777 2.169 2.133 0 3.772-2.249 3.772-5.495 0-2.873-2.064-4.882-5.012-4.882-3.414 0-5.418 2.561-5.418 5.207 0 1.031.397 2.138.893 2.738a.36.36 0 01.083.345l-.333 1.36c-.053.22-.174.267-.402.161-1.499-.698-2.436-2.889-2.436-4.649 0-3.785 2.75-7.262 7.929-7.262 4.163 0 7.398 2.967 7.398 6.931 0 4.136-2.607 7.464-6.227 7.464-1.216 0-2.359-.631-2.75-1.378l-.748 2.853c-.271 1.043-1.002 2.35-1.492 3.146C9.57 23.812 10.763 24 12 24c6.627 0 12-5.373 12-12 0-6.628-5.373-12-12-12z"
          />
        </svg>
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24">
          <path
            d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zM12 0C8.741 0 8.333.014 7.053.072 2.695.272.273 2.69.073 7.052.014 8.333 0 8.741 0 12c0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98C8.333 23.986 8.741 24 12 24c3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98C15.668.014 15.259 0 12 0zm0 5.838a6.162 6.162 0 100 12.324 6.162 6.162 0 000-12.324zM12 16a4 4 0 110-8 4 4 0 010 8zm6.406-11.845a1.44 1.44 0 100 2.881 1.44 1.44 0 000-2.881z"
          />
        </svg>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.copy-btn {
  border-radius: 8px;
  width: 80px;
  height: 30px;
  margin-right: 20px;
  margin-left: 20px;
}
.copied-btn {
  border-radius: 8px;
  width: 80px;
  height: 30px;
  background-color: navy;
  margin-right: 20px;
  margin-left: 20px;
}
.result-btns {
  display: flex;
  align-items: center;
  color: hsl(180, 66%, 49%);
  div {
    button {
      margin: 5px;
    }
  }
}
.mobile {
  display: none;
}
.card3 {
  margin-top: 100px;
}
.card2 {
  margin-top: 50px;
}
.result-link {
  margin-left: 20px;
}
h1,
p,
li,
div,
button {
  font-family: 'Roboto';
}
ul {
  list-style-type: none;
}
.buttonload {
  border: none;
  color: white;
  font-size: 16px;
}
.login {
  padding-right: 100px;
}
.home {
  width: 100%;
  // height: 100vh;
  display: flex;
  align-items: center;
  flex-flow: column;
}
.search-container {
  width: 100%;
  background-image: linear-gradient(
    top,
    white 50%,
    rgb(231, 231, 231) 50%,
    rgb(231, 231, 231)
  );
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: -2px;
}
.menu {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  div {
    display: flex;
  }
  li {
    float: left;
    padding: 10px;
    color: hsl(0, 0%, 75%);
    font-family: 'Poppins';
  }
  li:hover {
    cursor: pointer;
  }
}
.menu-logo {
  padding-left: 100px;
  align-items: center;
}
.header {
  display: flex;
  flex-flow: row;
  width: 100%;
  margin-bottom: 150px;
}
.greyish-bg {
  background-color: rgb(231, 231, 231);
  width: 100%;
  align-items: center;
  flex-flow: column;
  display: flex;
  padding-top: 100px;
  padding-bottom: 90px;
}
.whitish-bg {
  background-color: white;
  width: 100%;
  height: 100%;
}
.login-btn {
  background-color: transparent;
  color: hsl(257, 7%, 63%);
}
.header-img {
  img {
    width: 100%;
    padding-top: 90px;
  }
}
.search {
  height: 100px;
  width: 90%;
  top: 100%;
  display: flex;
  flex-flow: column;
  align-items: center;
  justify-content: center;
  border-radius: 10px;
  background: hsl(257, 27%, 26%) url('../assets/images/bg-shorten-desktop.svg');
  div {
    width: 70%;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .search-container {
    width: 100%;
  }
  input {
    width: 70%;
    height: 40px;
    border-radius: 12px;
    margin: 10px;
    padding-right: 20px;
    padding-left: 20px;
  }
  button {
    border-radius: 8px;
    margin-bottom: 0px;
  }
}
.error {
  color: hsl(0, 87%, 67%);
  display: flex;
  align-items: center;
  justify-content: flex-start !important;
  padding-left: 100px;
  font-style: italic;
}
.header-content {
  display: flex;
  width: 50%;
  align-items: flex-start;
  justify-content: center;
  flex-flow: column;
  padding-left: 100px;
  h1 {
    font-size: 50px;
    font-weight: 800;
    width:500px;
    letter-spacing:0.1mm ;
  }
  p {
    font-size: 15px;
    font-weight: 400;
    width:350px;
    color: hsl(0, 0%, 75%);
  }
}

.cards {
  width: 80%;
  display: flex;
  flex-flow: row;
  align-items: center;
  justify-content: space-between;
}
hr {
  width: 70%;
  height: 10px;
  position: absolute;
  overflow: hidden;
  background-color: hsl(180, 66%, 49%);
  border: none;
}
.card {
  z-index: 1000002;
}
.statics {
  width: 450px;
  height: 200px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 10px;
  flex-flow: column;
  h2 {
    color: hsl(257, 27%, 26%);
  }
  p {
    text-align: center;
    color: hsl(257, 7%, 63%);
  }
}
.boost {
  width: 100%;
  height: 40%;
  display: flex;
  flex-flow: column;
  align-items: center;
  justify-content: space-between;
  background: hsl(257, 27%, 26%) url('../assets/images/bg-boost-desktop.svg')
    no-repeat center;
  div {
    font-weight: 700;
    font-size: 28px;
    color: white;
    margin-top: 50px;
  }
}
button {
  background-color: hsl(180, 66%, 49%);
  width: 130px;
  height: 40px;
  font-weight: 700;

  color: white;
  border: none;
  border-radius: 30px;
  margin-bottom: 50px;
}
.footer {
  width: 100%;
  background-color: hsl(260, 8%, 14%);
  display: flex;
  align-items: center;
  justify-content: space-between;
  div {
    height: 200px;
    padding-top: 50px;
  }
  .logo {
    padding-left: 100px;
  }
}
.list {
  display: flex;
  color: hsl(0, 0%, 75%);
  font-size: 14px;
  .list-header {
    padding-bottom: 15px;
    color: white;
    font-size: 18px;
  }
}

.social {
  display: flex;
  width: 150px;
  align-items: flex-start;
  justify-content: space-between;
  padding-right: 150px;
}
svg {
  fill: white;
}
svg:hover {
  cursor: pointer;
  fill: hsl(180, 66%, 49%);
}
li:hover {
  color: hsl(180, 66%, 49%);
  cursor: pointer;
}
.list-header:hover {
  cursor: default;
  color: white;
}

.shorten-list {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-flow: column;
}
.search-result {
  width: 80%;
  height: 50px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: white;
  border-radius: 8px;
  margin: 10px;
  button {
    margin: 0;
    padding: 0;
  }
}

@media screen and (max-width: 1000px) {
  .mobile {
    display: inline;
  }
  .copy-btn {
    border-radius: 8px;
    width: 80px;
    height: 30px;
  }
  .copied-btn {
    border-radius: 8px;
    width: 80px;
    height: 30px;
    background-color: navy;
  }
  .result-link {
    margin-left: 0px;
  }
  .result-btns {
    display: flex;
    align-items: center;
    color: hsl(180, 66%, 49%);
    div {
      button {
        margin: 5px;
      }
    }
  }
  .menu-logo {
    padding-left: 10px;
  }
  .search-result {
    height: 100px;
    align-items: center;
    justify-content: space-around;
    flex-flow: column;
  }
  .overlay {
    height: 100%;
    width: 0;
    position: fixed;
    z-index: 1;
    left: 0;
    top: 0;
    background-color: rgb(0, 0, 0);
    background-color: rgba(0, 0, 0, 0.9);
    overflow-x: hidden;
    transition: 0.5s;
  }

  .overlay-content {
    position: relative;
    top: 15%;
    width: 100%;
    margin-top: 30px;
  }

  .overlay a {
    padding: 8px;
    text-decoration: none;
    font-size: 36px;
    color: #818181;
    display: block;
    transition: 0.3s;
  }

  .overlay a:hover,
  .overlay a:focus {
    color: #f1f1f1;
  }

  .overlay .closebtn {
    position: absolute;
    top: 20px;
    right: 45px;
    font-size: 60px;
  }

  .overlay a {
    font-size: 20px;
  }
  .overlay .closebtn {
    font-size: 40px;
    top: 15px;
    right: 35px;
  }
  .card3 {
    margin-top: 70px;
  }
  .card2 {
    margin-top: 70px;
  }
  .menu {
    margin-top: 40px;
  }
  .header {
    flex-flow: column-reverse;
    button {
      width: 200px;
      height: 50px;
      font-size: 20px;
    }
  }
  .search {
    width: 90%;
    height: 200px;
    div {
      flex-flow: column;
      width: 100%;
    }
    button {
      width: 78%;
    }
  }
  .header-content {
    width: 100%;
    align-items: center;
    padding-left: 0px;
    h1,
    p {
      padding: 0px;
      text-align: center;
    }
  }
  .cards {
    flex-flow: column;
    margin-top: 120px;
  }
  .footer {
    flex-flow: column;
    margin: 0;
    padding: 0;
    .list {
      flex-flow: column;
    }
    div {
      height: 100%;
    }
    .logo {
      text-align: center;
      padding-left: 0px;
    }
  }
  .menu-item {
    display: none;
  }
  .login {
    padding-right: 10px;
    button {
      display: none;
    }
  }
  .header-img {
    img {
      width: 100%;
      height: 50%;
      padding-top: 90px;
    }
  }
  .statics {
    width: 70%;
    margin-bottom: 90px;
    margin-top: 90px;
    h2 {
      text-align: center;
      font-size: 40px;
      font-weight: 900;
    }
    p {
      font-size: 25px;
    }
  }
  .vl {
    border-left: 6px solid hsl(180, 66%, 49%);
    height: 90px;
    margin-bottom: -100px;
    // z-index: -1;
    overflow: hidden;
  }
  hr {
    display: none;
  }
  .social {
    padding-right: 0;
  }
  li {
    text-align: center;
  }
  ul {
    padding: 0;
  }
}
.overlay-content {
  flex-flow: column;
  display: flex;
  align-items: center;
  justify-content: flex-start;
}
</style>

<script>
import Card from '../components/Card'
import axios from 'axios'

export default {
  name: 'home',
  components: {
    Card
  },
  data: () => {
    return {
      copied: false,
      url: '',
      result: [],
      loading: false,
      error: false,
      errMSG: ''
    }
  },
  methods: {
    openNav () {
      document.getElementById('myNav').style.width = '100%'
    },
    closeNav () {
      document.getElementById('myNav').style.width = '0%'
    },
    shorten () {
      this.loading = true
      if (this.url === '') {
        this.error = true
        this.loading = false
      } else {
        this.error = false
        axios
          .post('https://rel.ink/api/links/', { url: this.url })
          .then(res => {
            console.log(`https://rel.ink/${res.data.hashid}`)
            this.result.push(`https://rel.ink/${res.data.hashid}`)
          })
          .catch(e => {
            console.log(e)
            this.error = true
            this.errMSG = e
          })
          .finally((this.loading = false))
      }
    },
    validateLinkAddress (e) {
      if (e.keyCode === 13) {
        // alert('Enter was pressed')
        this.shorten()
      } else if (e.keyCode === 50) {
        alert('@ was pressed')
      }
      this.log += e.key
    }
  }
}
</script>
